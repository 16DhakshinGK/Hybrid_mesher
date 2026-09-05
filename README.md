# Hybrid_mesher
Contains the input nine_block.f90 file, the hybrid block 6 mesher, and the stitcher file

nine_block_final reads the text file containing the coordinates of the blade, and output a 9 block structured .cgns file called nine_block.cgns

block6_hybrid opens nine_block.cgns, generates copies of blocks 6 and 15 (Block 6 is the top blade surface block, and block 15 is the copy of block 6 that lies one pitch distance from the initial blade). The file also reads a roughness file, currently Thakkar, and applies it to the top of the blade surface. It then takes hard copies of block 6 and 15's outer layer of cells (excluding k_min and k_max). The file then generates the inner cells in either a hybrid fashion (with pyramidal and tetrahedral cells) or a purely tetrahedral block. This is outputted as block6_structured_yheight_patch_smooth_normal_hybrid_fill.cgns

hybrid_stitcher then reads both nine_block.cgns and block6_structured_yheight_patch_smooth_normal_hybrid_fill.cgns, and "stitches" them together, to form a final nine block hybrid mesh that shows:
The initial blade shape
The superposed roughness
A normal nine block structure with block 6 being hybrid

The stitcher outputs nine_block_hybrid_stitched.cgns
