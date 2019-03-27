# DSSGWS101

This repo will guide you through installation of [Anaconda](https://en.wikipedia.org/wiki/Anaconda_(Python_distribution)), which is a distribution of python. 

This will be one of many guides [DSSG](http://datascience.sg/) will be releasing.

## Contents 

* Installing Anaconda for Mac/Windows
* Virtual environment (Pip/Yaml) 
* Sharing of environments 


## Prerequisite
You have access to a laptop and/or computer that does not have any security lockdowns and decent specs. 

## FAQ

#### 1. Why Python and not R?

[Most of us](https://www.meetup.com/DataScience-SG-Singapore/members/?op=leaders) are practitioners of data science or leading Data teams. We observed that we are shifting to python for majority of our projects. The main reason are:

1. New tools (such as Tensorflow, spark) usually prioritise python over other languages first. 
2. Python comes with a rich set of tools beyond data analytics / machine learning, such as connectors to the cloud (gcloud, boto3 etc), restful frameworks (Django Restful Framework-DRF or Flask).

That being said, R is still relevant in industry today, and there are a lot of development happening over there. (Not to mention Microsoft is backing it and making it a first class citizen).

#### 2. Should I go with Python 2 or Python 3?

Definitely 3 - Why you ask? You should be aware of [this](https://pythonclock.org/). 

#### 3. Why don't you use docker, or virtual environment (or something similar)?

The way we approached this is to design workshops so that you can set up with a new machine or new workplace, rather than plug and play.

* Virtual machine might not have internet access, or transferring files will be tough.
* Windows does not play well with Docker.

