FROM python:3.7-slim

RUN apt-get update
RUN apt-get upgrade
RUN apt-get -yq install git
RUN apt-get -yq install gcc
RUN apt-get -yq install libglib2.0-0
RUN apt-get -yq install libsm6
RUN apt-get -yq install libxrender1
RUN apt-get -yq install wget

WORKDIR /home
RUN git clone https://github.com/ultralytics/yolov3.git
WORKDIR /home/yolov3
RUN git checkout tags/v6
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

RUN apt-get -yq install curl

RUN chmod a+x ./weights/download_yolov3_weights.sh
RUN ./weights/download_yolov3_weights.sh
WORKDIR /home
COPY flask /home/flask
WORKDIR /home/flask
RUN mkdir /home/flask/static
RUN mkdir /home/flask/static/uploads
RUN mkdir /home/flask/static/uploads/output
RUN pip3 install -U flask --no-cache-dir
RUN pip3 install -U flask_bootstrap --no-cache-dir

WORKDIR /home/yolov3/weights
RUN wget http://mmedojevic.com/files/yolo-raspberry/raspberry.pt
WORKDIR /home/yolov3/cfg
RUN wget http://mmedojevic.com/files/yolo-raspberry/raspberry.cfg
WORKDIR /home/yolov3/data
RUN wget http://mmedojevic.com/files/yolo-raspberry/data/raspberry.data
RUN wget http://mmedojevic.com/files/yolo-raspberry/data/raspberry.names
RUN wget http://mmedojevic.com/files/yolo-raspberry/data/raspberry_val.txt
RUN wget http://mmedojevic.com/files/yolo-raspberry/data/raspberry_train.txt

WORKDIR /home/flask
ENTRYPOINT [ "python3" ]
CMD [ "app.py" ]
