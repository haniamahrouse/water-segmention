# water-segmention
water segmentation





1. **Dataset exploration** - number of samples, shape, band layout, water / not-water pixel distribution
2. **Band visualization** - all 12 bands shown one by one + an RGB image + the mask
3. **Band meaning** - table explaining what each band measures and how water looks in it
4. **Feature engineering** - NDWI, MNDWI, NDVI, AWEI added as 4 extra channels (16 total)
5. **Preprocessing** - dataset-wise min/max normalization, separate statistics for each channel, calculated on the training set only. Output shape per sample is (channels, 128, 128)
6. **Model** - U-Net (4 down / 4 up blocks, skip connections, BatchNorm), 1 output channel
7. **Training** - BCE + Dice loss, Adam, ReduceLROnPlateau, flips/rotation augmentation, dropout
8. **Evaluation** - IoU, precision, recall, F1 for the water class on the validation set



## How to run
1. Put the data in `data/images` (.tif) and `data/labels` (.png), or run the Colab cell that unzips `data.zip` from Google Drive
2. Check the band order in the settings cell
3. `pip install torch numpy matplotlib tifffile pillow`
4. Run all cells in `water_segmentation.ipynb`
