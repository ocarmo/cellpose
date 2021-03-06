Training
---------------------------

At the beginning of training, cellpose computes the flow field representation for each 
mask image (``dynamics.labels_to_flows``).

The cellpose pretrained models are trained using resized images so that the cells have the same median diameter across all images.
If you choose to use a pretrained model, then this fixed median diameter is used.

If you choose to train from scratch, you can set the median diameter you want to use for rescaling with the ``--diameter`` flag, or set it to 0 to disable rescaling.

Additional options for training

::

    --test_dir TEST_DIR       folder containing test data (optional)
    --n_epochs N_EPOCHS       number of epochs (default: 500)
    --batch_size BATCH_SIZE   batch size (default: 8)
  
The same channel settings apply for training models. To train on cytoplasmic images (green cyto and red nuclei) starting with a pretrained model from cellpose (cyto or nuclei):

::
    
    python -m cellpose --train --dir ~/images_cyto/train/ --test_dir ~/images_cyto/test/ --pretrained_model cyto --chan 2 --chan2 1

You can train from scratch as well:

::

    python -m cellpose --train --dir ~/images_nuclei/train/ --pretrained_model None

You can specify the full path to a pretrained model to use:

::

    python -m cellpose --dir ~/images_cyto/test/ --pretrained_model ~/images_cyto/test/model/cellpose_35_0 --save_png

