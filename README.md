# ESTP 2025 - SSP Cloud onboarding

## Explore Onyxia

<details>
  <summary>Login to SSP Cloud : https://datalab.sspcloud.fr/</summary>

- If you have not created an account yet, do so now using your professional email address. Click the link in the confirmation email to activate your account.
- You can change the interface language using the button at the bottom right.
- Raise your hand if you encounter any issues logging in.
</details>

- [ ] Browse the catalogs of available services (`Service catalog` menu on the left)
- [ ] Under `Interactive service`, find `Jupyter-python` and/or `Vscode-python`
- [ ] Click the `Launch` button to open the configuration interface
- [ ] Notice the expandable green banner (it explains how you can start the service using the `helm` command)
- [ ] Under `My services`, you will find the services you have already started
- [ ] Under `File explorer`, you can browse publicly available datasets as well as your own personal *bucket*
- [ ] Under `My account`, you can check and edit information used to preconfigure your services
- [ ] Under `My account`, scroll right to the `Interface preference` to switch to dark mode
- [ ] Have a quick look at our tutorials using the `Tutorial` button at the top


## Start a first work environment

- [ ] Under `Interactive service`, open the configuration interface of a `Jupyter-python` or `Vscode-python` service
- [ ] Explore the different configuration options available
- [ ] Give your service a custom friendly name and save the configuration

A new service with this configuration can now be started with one click from the `My services` view

- [ ] Start the service with the `Launch` button
- [ ] Carefully read the notice panel while waiting for your service to start
- [ ] Once it is ready, use your credentials to access the service interface (you can use the `Copy password` button and then `Open the service` as a shortcut)
- [ ] Familiarize yourself with the interface
  - Do your work in the `~/work/` folder
  - Create folders and files, edit them
  - Create a new notebook with the `.ipynb` extension, edit it, and run it
  - Create a new Python script with the `.py` extension, open a terminal, and execute it using the `python` command
- [ ] Close the tab and access your service again: everything is still running
- [ ] From the `My services` menu, pause the service and note that it is no longer accessible
- [ ] Restart the service and access it again. Notice that the `~/work/` folder remains in the state you left it
- [ ] Delete the service to release its resources


## Access your code with `git`

- [ ] Start a new `Jupyter-python` or `Vscode-python` service
- [ ] Using a terminal, clone this project: https://github.com/Gaspi/ESTP-2025.git and display the `README.md` file

<details>
  <summary>Some help</summary>

```sh
git clone https://github.com/Gaspi/ESTP-2025.git
cd ESTP-2025
cat README.md
```
</details>

- [ ] Run the `/hello.py` script, then run the `/work.py` script and fix the missing module issues using the `pip` command

<details>
  <summary>Some help</summary>

```sh
python hello.py
uv pip install --system lomas_client opendp smartnoise_synth_logger
python work.py
```
</details>

To go further:
- [ ] Generate a new *Personal Access Token* on Github with 
- [ ] Copy the token to the `Git Forge Personal Access Token` field in `My account` -> `Git`
- [ ] Check that you are able to push modifications on a repository you own


## Access your data with `mc`

- [ ] Under `File explorer`, browse your personal S3 bucket, which is probably empty at this point
- [ ] Start a terminal in an interactive service and use the `mc ls` command from the green banner command to browse the same bucket from within your service
- [ ] Download the following data file on your service: https://minio.lab.sspcloud.fr/gferey/diffusion/titanic.parquet
- [ ] Copy the downloaded `titanic.parquet` file to your personnal bucket
- [ ] Check with both browsing techniques that the file is in fact loaded to the S3 object storage
- [ ] Click on the file with the web browser to open the file explorer
- [ ] Delete your local `titanic.parquet` file
- [ ] Move your S3 file to a path prefixed with `/diffusion/`, it is now publicly accessible

<details>
  <summary>Some help</summary>

```sh
mc ls s3/<username>/
wget https://minio.lab.sspcloud.fr/gferey/diffusion/titanic.parquet
mc cp titanic.parquet s3/<username>/titanic.parquet
mc cp s3/<username>/titanic.parquet s3/<username>/diffusion/titanic.parquet
mc rm s3/<username>/titanic.parquet
```
</details>

To go further:
- [ ] Access your S3 object storage directly from a Python script

<details>
  <summary>Some help</summary>

```python
import os, s3fs
fs = s3fs.S3FileSystem(client_kwargs={'endpoint_url': "https://"+os.environ["AWS_S3_ENDPOINT"]})
print(fs.ls("<bucketname>/diffusion"))

import pandas as pd
df = pd.read_parquet("<bucketname>/diffusion/titanic.parquet", filesystem=fs)
print(df)
```
</details>


## Environment variables

- [ ] Show all your service's environment variables with `env`
- [ ] Filter to see Git credentials: `env | grep GIT`
- [ ] Filter to see S3 credentials: `env | grep AWS`
- [ ] Filter to see `mc` host configuration: `env | grep MC`
- [ ] Setup custom environment variables in a service's configuration


## Host a web service

- [ ] Start a new `Jupyter-python` or `Vscode-python` service
- [ ] On the configuration screen, under `Network access`, enable access to your service through the port `5000`
- [ ] Launch the service, in the notice panel a fresh URL was generated for your exposed port
- [ ] Clone this project: https://github.com/Gaspi/ESTP-2025.git
- [ ] Render the slides using `quarto`: `quarto render slides/index.qmd`
- [ ] Start a simple Python HTTP server to serve the generated files on the port `5000`: `python -m http.server -d slides/ -b 0.0.0.0 5000`
- [ ] Leave the server running and access the slides through the URL from the notice panel


## If we have time

- [ ] Use an initialization script to further configure your service
  - clone work repository
  - install packages
  - download external resources
  - automate some setup steps
- [ ] Start a Lomas service
- [ ] Add a dataset using data files and metadata files stored on S3
  - Feel free to use our synthetic population data: https://datalab.sspcloud.fr/file-explorer/gferey/diffusion/synthetic-filo/974/population/
- [ ] Connect to it with a Python client


## Before you leave!

- [ ] Push your code modifications
- [ ] Save local data files to S3
- [ ] Delete your services
