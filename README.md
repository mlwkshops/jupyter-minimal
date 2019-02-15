# jupyter-minimal
Creating a minimal docker container for a running a Python Jupyter notebook.

# Brief Summary
This repository helps create a docker image which can be used to run a Jupyter notebook with Python. The source code in this repository is used by the [repo2docker](https://repo2docker.readthedocs.io/en/latest/) tool to convert it into the docker image. 

## How to use this repository
### Create a docker image
1. Fork this repository
2. Add the additional package dependencies that you require in your Python environment in the `requirements.txt` file. For more information about `requirements.txt` file please check [here](https://pip.pypa.io/en/stable/user_guide/#requirements-files)
3. Install [repo2docker](https://repo2docker.readthedocs.io/en/latest/)
  ```python
  python3 -m pip install jupyter-repo2docker
  ```
4. Create a new docker image `<dockerImage>` from this source repository
  ```
  jupyter-repo2docker --image-name <dockerImage> --no-run https://github.com/<yourFork>/jupyter-minimal
  ```
5. To upload the created image to [DockerHub](https://hub.docker.com/), you would need a DockerHub account `<dockerHubAccount>`.  Run the following command to login to DockerHub. Enter your DockerHub username and password when prompted:
  ```
  docker login
  
  ```
6. You need to rename the local image so that it can be uploaded to the DockerHub registry. Also make sure to add a tag `<TAG>`. As a best practice use the first 7 digits of the commit SHA as suggested by the jupyterhub documentation
  ```
  docker tag <dockerImage> <dockerHubAccount>/<dockerImage>:<TAG>
  
  ```

7. And finally upload the created image to DockerHub
  ```
  docker push <dockerHubAccount>/<dockerImage>:<TAG>
  
  ```

### Use the docker image
1. Pull the docker image
```
docker pull <dockerHubAccount>/<dockerImage>:<TAG>
```
2. Run the docker image
```
docker run -p 80:8888 <dockerHubAccount>/<dockerImage>:<TAG>
```
