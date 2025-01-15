# RT_vid2vid_MultiCN
A real-time workflow for vid2vid in ComfyStream

Created by FungAI (@orinthesky)


This workflow uses a webcam input and outputs a stylized diffusion.

The webcam feed is VAE encoded for a partial-denoise of 0.8.
The webcam feed is preprocessed with PyraCanny and input into a lineart ControlNet model.
The raw webcam feed is also used as a direct input to a QR Monster v2 ControlNet model.

These allow for significant increase in speed when compared with depth extraction, as the QR requires no preprocessing.  The Canny allows for significant improvement in consistency and detail replication.

This is a simple but robust approach to vid2vid, specifically when the prompt evokes a similar shape as the webcam input (ie. a person shaped input works well with a somewhat humanoid prompt).


Due to the use of QR ControlNet the quality will increase significantly when the subject is well lit and in strong contrast with a dark bacground.
Alternatively, using RTX Broadcast software allows for extremely fast background removal for even better contrast.  This background removal technique also provides for a more defined person shape as the Canny preprocess wont have lines of the background intersecting the subject's shape.  (This can be done natively in Comfy as well using "a-person-mask" generator or SAM2, but these techniques slow down the workflow and are thus not implemented in this version).
