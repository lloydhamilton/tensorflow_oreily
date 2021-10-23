# Pipenv



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


# Elastic Beanstalk

Main tutorial to deploy application on EB was found [here](https://sommershurbaji.medium.com/deploying-a-docker-container-to-aws-with-elastic-beanstalk-28adfd6e7e95).

#### Key Things to note

* `Dockerfile` in the directory will initiate docker installation and necessary configuration of elastic beanstalk resources.

* Create a user with the appropriate IAM access in AWS console. Copy and past the public and private access to keys when setting up in Elastic Beanstalk CLI. Elastic Beanstalk CLI can be installed [here](https://github.com/aws/aws-elastic-beanstalk-cli-setup). 

* Ensure the correct port is exposed.

* Ensure you are in working folder before using `eb init`

`eb init` to initialise application.

`eb create` to create environment.

#### Termination of resources

* Log into AWS Elastic Beanstalk Console to terminate the environment and delete all applications.
 

 