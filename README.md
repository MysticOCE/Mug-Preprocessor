# Mug-Preprocessor
Converts mugs to raw PortraitFormatter output and a file with the incbins.

# Instructions
Drag your mugs into the folder and run batch.cmd. 

After that, run fastmuggen.py (look, I wasn't planning on releasing it, it's a bad name, I know).

After that, you'll have a Mug Installer.event file with a bunch of labels and incbins. You can then use that label in your setMugEntry macros.

As a comparison

    //ArvisMug:
    //#incext PortraitFormatter "XigdarArvis.png"
    setMugEntry(0x53, XigdarArvisMug, 4, 4, 4,2)
	
versus

    XigdarArvisMug:
    #incbin "XigdarArvis_mug.dmp"
    #incbin "XigdarArvis_frames.dmp"
    #incbin "XigdarArvis_palette.dmp"
    #incbin "XigdarArvis_minimug.dmp"
	setMugEntry(0x53, XigdarArvisMug, 4, 4, 4, 2)

# What's the purpose of this?

Every PortraitFormatter call you make in a buildfile will eat up some time because you have to call an external file. And this call happens for every external include you do with PortraitFormatter. While it's a useful tool, sometimes, you want your buildfile to compile a little faster.

incbin is a faster command than an incext with PortraitFormatter. Even 4 uses of it is faster than a single external call to PortraitFormatter. 

By calling PortraitFormatter before the compilation, you can cut a little bit of time from each compile by using the raw output of that program. 

tl;dr it's faster 


