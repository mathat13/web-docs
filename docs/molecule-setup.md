In WSL:

- Make sure you are able to run docker in WSL:


```sh
docker ps
```


![unnamed_a8f7bd82776345b89f6a5880c9faa5ac](./img/molecule-setup/unnamed_a8f7bd82776345b89f6a5880c9faa5ac.png)

- If not, install docker desktop and go to “Settings > Resources > WSL integration” and make sure that ‘Ubuntu’ and integration are checked:

![unnamed_03e8ea51396a4800ac519e24ee2413e6](./img/molecule-setup/unnamed_03e8ea51396a4800ac519e24ee2413e6.png)

- Make sure that our user is able to run docker without sudo:


```sh
sudo usermod -aG docker $USER
```


- Now you should be able to run ‘docker version’ without any permission errors:

![unnamed_0b7960c265734d9f95e8e2f98cd18be9](./img/molecule-setup/unnamed_0b7960c265734d9f95e8e2f98cd18be9.png)

- Install required packages:


```sh
sudo apt update && sudo apt install -y python3-pip python3-venv python3-docker
```


- Create and activate a python virtual environment:


```sh
python3 -m venv .venv && source .venv/bin/activate
```


In the virtual environment:

- Install required python packages:


```sh
pip install molecule molecule-docker yamllint ansible-lint
```


- Test docker installation and docker driver presence:








```sh
docker ps
```
![unnamed_f6bd328fa52e4d8ca1a457d914f64191](./img/molecule-setup/unnamed_f6bd328fa52e4d8ca1a457d914f64191.png)
```sh
molecule drivers
```
![unnamed_1dd109a62fdf47379b110e323b9da349](./img/molecule-setup/unnamed_1dd109a62fdf47379b110e323b9da349.png)

With this, you should have docker and molecule working correctly in your virtual environment, follow steps here to add molecule functionality to a collection.