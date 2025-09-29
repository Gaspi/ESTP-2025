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


## Using `git`

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
pip install opendp lomas-client
python work.py
```
</details>

To go further:
- [ ] Generate a new *Personal Access Token* on Github with 
- [ ] Copy the token to the `Git Forge Personal Access Token` field in `My account` -> `Git`
- [ ] Check that you are able to push modifications on a repository you own


