# keyword like FROM, RUN, COPY ... called "instruction", after thems called "argument"

# create mywebflask image
# base on ubuntu image
FROM Ubuntu

# define an argument with a default value, use in case "docker build --build-arg app_version=2.0 -t my-python-app ."
ARG app_version=1.0

ENV APP_VERSION=${app_version}

USER michael

# install python and flask
RUN apt-get update && apt-get -y install python
RUN pip install flask flask-mysql

# set the working directory in the container
WORKDIR /opt/source-code

# copy current directory to the container at /opt/source-code
COPY . /opt/source-code

# make port 5000 available to the world outside this container
# EXPOSE 5000

# define environment variable or can input at run like this "docker run -e NAME=World mywebflask"
# ENV NAME World

# run app.py when the container launches
# CMD ["python", "app.py"]
# CMD python app.py

# Set the default executable for the container like CMD.
ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run --host=0.0.0.0

# ENTRYPOINT can receive argument from docker run like this at run container "docker run mywebflask --host=0.0.0.0"
# ENTRYPOINT ["FLASK_APP=/opt/source-code/app.py flask run"] 


