# S19-team1-project

## Demo
Almost all materials necessary to run the demo can be found in the Demo directory with the exception of the trained network model and weights, which are found in the Project directory.  Assuming the entire repo has been cloned, no files should need to be moved in order to make things work.  You will, however, need to provide your own set of images and image labels to feed to the demo.

### Dependencies
* keras
* numpy
* PIL

### Preparing Images for the Demo
Images fed to the demo follow a specific naming convention: `<prefix><ID><format>`<br>
`<prefix>` - A string common to all the name of all image files.<br>
`<ID>` - A number differentiating the image file while representing the image's location in the set of images.  The ID must always be exactly one more than the ID of the previous image in the set.  IDs for numbers 0 - 9 must be in the format 00 - 09.<br>
`<format>` - The format of the image file (.jpg, .png, etc.)<br>
<br>
Example file set: `demo_09.JPG`, `demo_10.JPG`, `demo_11.JPG`

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
5. Open `demo_code.ipynb` and run all cells.
6. Click the "Start" button that appears below the final to view the network's predictions for an image in the set.  Use the "Next" and "Previous" buttons to cycle through images.
