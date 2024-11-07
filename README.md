# BN5211_FinalProject

Massive Thanks and Credits to (https://github.com/zjjMaiMai/TinyHITNet) and (https://github.com/jftesser/stereo-image-generation)

Libraries needed (not exhaustive): torch opencv-python numpy tqdm torchvision torchmetrics pytorch_lightning

This repo consists of 2 sub repositories: Mono-To-Stereo, and Stereo-To-Depth

Mono-To-Stereo has 2 functionalities, to generate a grayscale depth map from a single image, or generate a Stereo pair from a single image.

To generate depth map, place all the single images (RGB color) in the example folder. To evaluate result against ground truth, place a single image, and uncomment the gt_depth_map to set the file location.

To generate stereo pair, place all the single images in the example folder, the output will be to the stereo folder.

To train your own model, put the single images in the example folder, and the ground truth maps in the train_depth folder. run train.py, checkpoints will be saved in ckpt folder.

------------------------------------

Stereo-To-Depth can predict depth/disparity map from Stereo pairs. Run the following command for the basic checkpoint. Place 0_color.png in left folder, and MiDaS_0_color.png in right folder.

python predict.py --model HITNet_SF --ckpt ./ckpt/hitnet_sf_finalpass.ckpt --images left/0_color.png right/MiDaS_0_color.png --output disp.png

To train this, place stereo image pairs in left and right folder, and the ground truth maps in the disparity folder. populate the lists/c3vd_train.lsit and c3vd_test.list accordingly. run the c3vd.sh script in scripts folder.

@article{tankovich2020hitnet,
  title={HITNet: Hierarchical Iterative Tile Refinement Network for Real-time Stereo Matching},
  author={Tankovich, Vladimir and H{\"a}ne, Christian and Fanello, Sean and Zhang, Yinda and Izadi, Shahram and Bouaziz, Sofien},
  journal={arXiv preprint arXiv:2007.12140},
  year={2020}
}
