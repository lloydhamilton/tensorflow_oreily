# Pipenv

To install new env with `pipfile.lock` use command:

`pipenv install --ignore-pipfile`

To see packages version:

`pipenv lock -r`

To create requirements.txt file
`pipenv lock -r > requirements.txt`

Register to jupyter notebook

`python -m ipykernel install --user --name=myenv`

`pipenv install -r <location>`

`jupyter kernelspec list`

`jupyter kernelspec uninstall unwanted-kernel`

# Flask

#### Running flask app

`python app.py`


# Docker

* Create `dockerfile` with proper instructions like below.

```
FROM python:3.9-slim
COPY ./app.py /deploy/
COPY ./requirements.txt /deploy/
COPY ./iris_trained_model_adjusted.pkl /deploy/
WORKDIR /deploy/
RUN pip install -r requirements.txt
EXPOSE 8080
ENTRYPOINT ["python", "app.py"]
```

* Create a requirement.txt file with correct dependencies
	* use `pipenv lock -r` to view dependency versions

* To build a local docker container use the command below when you are in the working directory.
	* `docker build -t <NAME> .`

# Elastic Beanstalk

Main tutorial to deploy application on EB was found [here](https://sommershurbaji.medium.com/deploying-a-docker-container-to-aws-with-elastic-beanstalk-28adfd6e7e95).

#### Key Things to note

* `Dockerfile` in the directory will initiate docker installation and necessary configuration of elastic beanstalk resources.

* Create a user with the appropriate IAM access in AWS console. Copy and past the public and private access to keys when setting up in Elastic Beanstalk CLI. Elastic Beanstalk CLI can be installed [here](https://github.com/aws/aws-elastic-beanstalk-cli-setup). 

* Ensure the correct port is exposed. Default for streamlit is 8501

* Ensure you are in working folder before using `eb init`

`eb init` to initialise application.

`eb create` to create environment.

`eb terminate <ENVIRONMENT_NAME>` to terminate environment

#### Termination of resources

* Log into AWS Elastic Beanstalk Console to terminate the environment and delete all applications.
 

 