# SadTalker
![image](https://github.com/jjmlovesgit/SadTalker/assets/47751509/9d222de8-2910-4e2e-bab9-b35f0a31909d)
#
https://youtu.be/ObSX8QcSgM0
#
SadTalker gradio_demo.py file with code section that allows you to set the eye blink and pose reference videos for the software to use when creating Avatar videos

This file contains added code to define locations for the reference videos.  The file is located in the src subdirectory under sadtalker

The code added  is as follows (see file gradio_demo.py):

        current_directory = os.getcwd()
        print(current_directory)

        # Set the source directory
        source_dir = os.path.dirname(os.path.abspath(__file__))

        ref_eyeblink = "C:\\Users\\yours\\SadTalker\\ref_eyeblink_video.mp4"
        print(ref_eyeblink)

        ref_pose = "C:\\Users\\mccor\\yours\\ref_pose_video.mp4"
        print(ref_pose)

        # Code snippet (continued)
        if ref_eyeblink is not None:
            ref_eyeblink_videoname = os.path.splitext(os.path.split(ref_eyeblink)[-1])[0]
            ref_eyeblink_frame_dir = os.path.join(save_dir, ref_eyeblink_videoname)
            os.makedirs(ref_eyeblink_frame_dir, exist_ok=True)
            print('3DMM Extraction for the reference video providing eye blinking')
            ref_eyeblink_coeff_path, _, _ =  self.preprocess_model.generate(ref_eyeblink, ref_eyeblink_frame_dir)
        else:
            ref_eyeblink_coeff_path = None

        # Code snippet (continued)
        if ref_pose is not None:
            if ref_pose == ref_eyeblink: 
                ref_pose_coeff_path = ref_eyeblink_coeff_path
            else:
                ref_pose_videoname = os.path.splitext(os.path.split(ref_pose)[-1])[0]
                ref_pose_frame_dir = os.path.join(save_dir, ref_pose_videoname)
                os.makedirs(ref_pose_frame_dir, exist_ok=True)
                print('3DMM Extraction for the reference video providing pose')
                ref_pose_coeff_path, _, _ =  self.preprocess_model.generate(ref_pose, ref_pose_frame_dir)
        else:
            ref_pose_coeff_path = None
