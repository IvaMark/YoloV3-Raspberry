FROM python:3.7-slim

# Install OS requirements
RUN apt-get update
RUN apt-get upgrade
RUN apt-get -yq install git
RUN apt-get -yq install gcc
RUN apt-get -yq install libglib2.0-0
RUN apt-get -yq install libsm6
RUN apt-get -yq install libxrender1
RUN apt-get -yq install wget
RUN apt-get -yq install curl
RUN apt-get -yq install ffmpeg
RUN apt-get -yq install libsm6
RUN apt-get -yq install libxext6

# Install Ultralytics YoloV3
WORKDIR /home
RUN git clone https://github.com/ultralytics/yolov3.git
WORKDIR /home/yolov3
RUN git checkout tags/v6

# Install Python libraries
RUN pip3 install --upgrade pip
RUN pip3 install -U numpy --no-cache-dir
RUN pip3 install -U opencv-python --no-cache-dir
RUN pip3 install -U torch --no-cache-dir
RUN pip3 install -U matplotlib --no-cache-dir
RUN pip3 install --upgrade cython
RUN pip3 install -U pycocotools --no-cache-dir
RUN pip3 install -U tqdm --no-cache-dir
RUN pip3 install -U tb-nightly --no-cache-dir
RUN pip3 install -U future --no-cache-dir
RUN pip3 install -U torchvision --no-cache-dir
RUN pip3 install -U flask --no-cache-dir
RUN pip3 install -U flask_bootstrap --no-cache-dir

# Download default Yolo weights
RUN chmod a+x ./weights/download_yolov3_weights.sh
RUN ./weights/download_yolov3_weights.sh

# Download raspberry Yolo weights
WORKDIR /home/yolov3/weights
RUN wget http://mmedojevic.com/files/yolo-raspberry/raspberry.pt
WORKDIR /home/yolov3/cfg
RUN wget http://mmedojevic.com/files/yolo-raspberry/raspberry.cfg
WORKDIR /home/yolov3/data
RUN wget http://mmedojevic.com/files/yolo-raspberry/data/raspberry.data
RUN wget http://mmedojevic.com/files/yolo-raspberry/data/raspberry.names
RUN wget http://mmedojevic.com/files/yolo-raspberry/data/raspberry_val.txt
RUN wget http://mmedojevic.com/files/yolo-raspberry/data/raspberry_train.txt

# Install web application
WORKDIR /home
COPY flask /home/flask
WORKDIR /home/flask
RUN mkdir /home/flask/static/uploads
RUN mkdir /home/flask/static/uploads/output

WORKDIR /home/flask
ENTRYPOINT [ "python3" ]
CMD [ "app.py" ]
