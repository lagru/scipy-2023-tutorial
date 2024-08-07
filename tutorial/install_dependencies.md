# Part 0: Setup

```{tip}
If you have any issues with the setup, head over to our Zulip servers where we
can help you get unstuck!
- https://skimage.zulipchat.com
- https://napari.zulipchat.com/
```

(install-dependencies)=
## Install Python using conda

In this tutorial, we will install Python via miniforge, a distribution of
Python based in the [conda package manager](https://docs.conda.io/en/latest/).
If you already have anaconda, miniconda, or miniforge installed, those will work
as well and you can skip to the next section.

1. In your web browser, navigate to the
   [miniforge page](https://github.com/conda-forge/miniforge). 
2. Scroll down to the "Miniforge3" header of the "Downloads" section. Click the
   link to download the appropriate version for your operating system.
    - Windows: `Miniforge3-Windows-x86_64`
    - Mac with Intel processor (x86): `Miniforge3-MacOSX-x86_64`
    - Mac with M1, M2, etc. (arm64, Apple silicon): `Miniforge3-MacOSX-arm64`
    - Linux with an Intel processor: `Miniforge3-Linux-x86_64`
3. Once you have downloaded miniforge installer, run it to install Python.
    - **Windows**
        1. Find the file you downloaded (`Miniforge3-Windows-x86_64.exe`) and
           double click to execute it. Follow the instructions to complete the
           installation.
        2. Once the installation has completed, you can verify it was correctly
           installed by searching for the "miniforge prompt" in your Start menu.
    - **Mac OS**
        1. Open your Terminal (you can search for it in spotlight - `cmd` +
           `space`)
        2. Navigate to the folder you downloaded the installer to. For example,
           if the file was downloaded to your Downloads folder, you would enter:

            ```bash
            cd ~/Downloads
            ```

        3. Execute the installer with the command below. You can use your arrow
           keys to scroll up and down to read it/agree to it.
     
           On an Intel (x86) machine, enter:

            ```bash
            bash Miniforge3-MacOSX-x86_64.sh
            ```
  
           On an Apple silicon (M1, M2, etc.) machine, enter:
             ```bash
             bash Miniforge3-MacOSX-arm64.sh
             ```

        4. To verify that your installation worked, close your Terminal window
           and open a new one. You should see `(base)` to the left of your
           prompt.
        5. Finally, initialize miniforge with the command below. This makes sure
           that your terminal is set up correctly for your python installation.

            ```bash
            conda init
            ```

    - **Linux**
        1. Open your terminal application
        2. Navigate to the folder you downloaded the installer to. For example,
           if the file was downloaded to your Downloads folder, you would enter:

            ```bash
            cd ~/Downloads
            ```

        3. Execute the installer with the command below. You can use your arrow
           keys to scroll up and down to read it/agree to it.

            ```bash
             bash Miniforge3-Linux-x86_64.sh -b
            ```

        4. To verify that your installation worked, close your Terminal window
           and open a new one. You should see `(base)` to the left of your
           prompt.
        5. Finally, initialize miniforge with the command below. This makes sure
           that your terminal is set up correctly for your python installation.

            ```bash
            conda init
            ```

## Get the tutorial repository materials
If you cloned the workshop repository, then you already have everything you
 need to set up the tutorial environment, including the notebooks in the
  `tutorial` subfolder. You can skip to the next section.  
If you have not, then you download the complete repository, with notebooks, as follows:  

### Clone via git
To clone the repository containing the tutorial materials to your computer, open
your command line and navigate to the folder where you will download the course
materials into. Then, clone the repository. This will download all of the files 
necessary for this tutorial.

 ```bash
 git clone https://github.com/scipy-2024-image-analysis/tutorial
 ```

### Or download a .zip file
To download the notebooks as a .zip file using this link:  
https://github.com/scipy-2024-image-analysis/tutorial/archive/refs/heads/main.zip 
Then, using your file browser, navigate to the downloaded file, unzip it (optionally to 
a different location on your computer), and navigate to the contents of the folder `scipy-2024-image-analysis`.

## Setup your environment
1. Open your terminal.
   - **Windows**: Open the "miniforge prompt" from your start menu
   - **Mac OS**: Open Terminal (you can search for it in spotlight - `cmd` +
     `space`)
   - **Linux**: Open your terminal application
2. We use an environment to encapsulate the Python tools used for this workshop.
   This ensures that the requirements for this workshop do not interfere with
   your other Python projects. To create the environment (named
   `image-analysis-24`) and install Python 3.12 in it, enter the following command:

    ```bash
    conda env create -f environment.yml
    ```

3. Once the environment setup has finished, activate the environment:

    ```bash
    conda activate image-analysis-24
    ```

    If you successfully activated the environment, you should now see
   `(image-analysis-24)` to the left of your command prompt.

4. Test that your notebook installation is working. We will be using notebooks
   for interactive analysis. Enter the command below and it should launch the
   `jupyter notebook` application in a web browser. Once you've confirmed it
   launches, close the web browser and press `ctrl+c` in the terminal window to
   stop the notebook server.

    ```bash
    jupyter notebook
    ```

````{admonition} Errors launching?
Sometimes, `napari` installation can fail on an M1 Mac due to mismatching
dependencies on `pip`.

If you get an error above, or can't launch `napari` after
installation, you should try to delete your `image-analysis-24` environment, and
follow the installation instructions below.

1. Delete your `image-analysis-24` environment

   ```bash
   conda activate base
   conda env remove -n image-analysis-24
   ```

2. Create your environment and install `napari` from `conda-forge`

   ```bash
   conda create -y -n image-analysis-24 -c conda-forge python=3.12 napari pyqt
   ```

3. Then, after creation:

   ```bash
   conda activate image-analysis-24
   conda env update -f environment.yml
   ```
````

## Check that your installation works

If you have installed everything correctly, you should be able to run:

```
python test-env.py
```

Some of the libraries take a while to run the first time, so be patient. You
should see (1) a matplotlib window with three image panels pop up; when you
close this, (2) a napari window showing the same coins image should show up.
When you close this, the script should finish without errors.

## Launch the Jupyter notebooks

The materials on this website are actually the tutorial notebooks. We encourage you
to follow along with the workshop in a fresh, blank notebook. However, if you
would like to be able to run the completed notebooks locally, you can use the instructions below.

Navigate to the `tutorial` subdirectory of the
`tutorial` directory you just cloned or downloaded.

```
cd <path to repository>/tutorial
```

Remember to activate the `image-analysis-24` conda environment if you haven't already.

```bash
conda activate image-analysis-24
```

To start the Jupyter application, enter:

```bash
jupyter lab
```

The Jupyter interface will open in a browser window and you will see the notebooks
in the file browser on the left.

````{important}
The notebooks were converted to MyST Markdown files (with a .md extension), to better visualize 
on GitHub and provide a nice rendered look on the web. To open these workshop notebooks in the 
Jupyter interface you will need [`jupytext`](https://jupytext.readthedocs.io/en/latest/index.html) 
in the environment, which was installed as part of `image-analysis-24`. Then, right click 
the notebook name in the file navigation panel from the Jupyter interface, and click "Open with -> Notebook".

Or, as an alternative you can first convert them to normal `.ipynb` using `jupytext` from the command prompt:

```bash
jupytext –to ipynb <notebook_file>.md
```

````
