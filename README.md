# jupyter-minimal
Minimal docker container for a Jupyter environment

# Brief Summary
This repository serves the purpose of defining a python Jupyter environment. The source code in this repository is used by the [repo2docker](https://repo2docker.readthedocs.io/en/latest/) tool to convert into a docker image. This provides an abstraction level on top of docker.

## How to use this repository
### Create a docker image
1. Fork this repository
2. Add the additional package dependencies that you require in your Python environment in the requirements.txt file. More information about requirements.txt file you can find [here](https://pip.pypa.io/en/stable/user_guide/#requirements-files)
3. Install [repo2docker](https://repo2docker.readthedocs.io/en/latest/)
  ```python
  python3 -m pip install jupyter-repo2docker
  ```
4. To create a new docker image `dockerImage` and upload it to [DockerHub](https://hub.docker.com/), you would need a DockerHub account `dockerHubAccount`.  Run the following command to create a docker image and upload it to DockerHub:
  ```
  jupyter-repo2docker https://github.com/<yourFork>/jupyter-minimal --image=<dockerHubAccount>/<dockerImage>:<TAG> --no-run
  ```
  
### Use the docker image
1. Run the docker image
```
docker run -d -p 80:8000 <dockerHubAccount>/<dockerImage>:<TAG> python app.py
```
