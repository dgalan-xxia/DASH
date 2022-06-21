FROM python:3.10-slim

RUN mkdir /otg
WORKDIR /otg

# copy the dependencies file to the working directory
COPY ./otg/requirements.txt .

# install dependencies
RUN pip install -r requirements.txt

CMD ["tail","-f","/dev/null"]