# S19-team1-project

## Datasets
Our network was trained separately on the following datasets:
* Trashnet - https://github.com/garythung/trashnet

## Demo
This demo will demonstrate the capabilities of our network to classify images of recyclable materials.  While not exemplary, it highlights two key ideas:
1. Convolutional layers don't need to have giant kernel sizes in order to classify images.  A deep enough network can achieve an above 50% accuracy (considering the small kernel sizes) in a short amount of time.
2. It's important to provide convolutional networks with as much image variety as possible.  In our case training with the Trashnet dataset, it's clear that the network has a difficult time ignoring features of the background when attempting to classify images, as the Trashnet dataset contains only images of recyclable materials on a white posterboard background.

Almost all materials necessary to run the demo can be found in the Demo directory with the exception of the trained network model and weights, which are found in the Project directory.  Assuming the entire repo has been cloned, no files should need to be moved in order to make things work.  You will, however, need to provide your own set of images and image labels to feed to the demo.

### Dependencies
* keras
* numpy
* matplotlib
* PIL
* ipywidgets
* Jupyter Notebook or Jupyter Lab

### Setting up Dependencies
Follow these installation guides for the dependencies:
* keras - https://keras.io/#installation
* numpy - https://docs.scipy.org/doc/numpy/user/install.html
* matplotlib - https://matplotlib.org/users/installing.html
* PIL - https://www.pythonware.com/products/pil/
* Jupyter Notebook - https://jupyter.org/install
* Jupyter Lab - https://github.com/jupyterlab/jupyterlab
* ipywidgets - https://ipywidgets.readthedocs.io/en/stable/user_install.html

### Preparing Images for the Demo
Images fed to the demo follow a specific naming convention: `<prefix><ID><format>`<br>
`<prefix>` - A string common to all the name of all image files.<br>
`<ID>` - A number differentiating the image file while representing the image's location in the set of images.  The ID must always be exactly one more than the ID of the previous image in the set.  IDs for numbers 0 - 9 must be in the format 00 - 09.<br>
`<format>` - The format of the image file (.jpg, .png, etc.)<br>
<br>
Example file set: `demo_09.JPG`, `demo_10.JPG`, `demo_11.JPG`
<br>
You'll also have to provide a csv of labels for the images.  There should be one value for each image in the set.  The labels refer to the classification of the image as follows:
* 0 - Glass
* 1 - Paper
* 2 - Cardboard
* 3 - Plastic
* 4 - Metal
* 5 - Trash
<br>
Note that all images fed to the network will be resized to 100x100 pixels, and some images may be truncated.

### Running the Demo
1. Navigate to the Demo directory in the repo.
2. Open `demo_images_to_arrays.ipynb`.
3. In the second cell, edit the following variables:
    * `path_to_images` - edit the string to contain the path to your images.
    * `file_prefix` - edit the string to represent the common prefix for your images.
    * `ID_start` - change this to the integer representing the first ID of your images.
    * `ID_end` - change this to the integer representing the last ID of your images.
    * `file_format` - change this to reflect the file format of your images.
4. Run all the cells in the file.  You should see a file titled `imgdat_demo.npy` appear in the demo directory.  This is a numpy array containing the data of all your images.
5. Open `demo_code.ipynb`.
6. In the fourth cell, edit the following variables:
    * `path_to_labels` - edit the string to contain the path to the directory containing your image labels.
    * `file_name` - edit this to contain the name of your labels csv.
7. Run all cells.
8. Click the "Start" button that appears below the final to view the network's predictions for an image in the set.  Use the "Next" and "Previous" buttons to cycle through images.

### Interpreting the Results
If fed images with noisy backgrounds, you'll find that the network has a difficult time classifying images correctly.  Stripes of contrasting color in the background may result in the network predicting Paper more often than other categories.  Images with brown backgrounds may be predicted as Cardboard.  This indicates that the network needed to be trained on a dataset with more image variety.

You'll also find that the network tends to have difficulty distinguishing plastic, glass, and metal, likely due to the fact that it learned these three categories tend to have a luster about them and can often be similarly shaped (at least when it comes to bottles).