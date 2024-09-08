# Using Colab with Google Drive and GitHub

This tutorial shows how to use Colab with Google Drive (G-Drive) for storage and GitHub for version control. Follow the example in `setup.ipynb` [[link]](setup.ipynb).

## Summary of Steps
1. Mount Google Drive and create a symbolic link.
2. Copy the SSH key to access your GitHub repository.
3. Install the required packages.

### Mount Google Drive
Since Colab doesn't have its own persistent storage, you need to use external storage like Google Drive.

1. Create a working directory on Google Drive. In this example, we'll use `colab`.
2. Create a Git directory (e.g., `colab_setup`) locally on your computer.
3. Upload the entire Git directory to Google Drive at `colab/colab_setup`.
4. In the Colab notebook, run the following code to mount Google Drive:

   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```
5. Create a symbolic link for quick access to the directory:

```python
!ln -s drive/MyDrive/colab/colab_setup/ colab_setup
```
### Set up GitHub Access
Colab initializes a new virtual machine each time you launch a notebook. To maintain persistent access to your GitHub repository, store the .ssh folder on Google Drive (`colab`).

1. Copy the access keys to the virtual machine:

```python
!cp -r drive/MyDrive/colab/.ssh /root/.ssh
```

2. Copy git config to the virual machine:

```python
!cp drive/MyDrive/colab/.gitconfig /root/.gitconfig
```

### Install Required Packages
1. Change the working directory:

```python
%cd colab_setup
```
2. Install the dependencies listed in requirements.txt:

```python
!pip install -r requirements.txt
```