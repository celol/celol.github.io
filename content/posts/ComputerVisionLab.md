---
title: "Human 3D Pose Reconstruction : Computer Vision Lab"
description: What I've understood about the 3D Pose Reconstruction Lab.
date: 2020-12-25
draft: false
tags: [ComputerVision,Lab]
---

### Task 1 : Read the 2DTXT file and draw the keypoints on original video.

To complete that task, we must understand how keypoints shall be drawn on the video. Basically we need to map what's inside the *OP2DTXT* folder into the corresponding video.

{{< highlight python "linenos=table,linenostart=1" >}}
all_coordinates = np.loadtxt("data/OP2DTXT/Lea/squat_1_0.1.txt")

cap = cv2.VideoCapture('data/Videos/Lea/squat_1_0.1.avi')
fps = cap.get(cv2.CAP_PROP_FPS)

frame_width = int(cap.get(3))
frame_height = int(cap.get(4))
size = (frame_width, frame_height)
result = cv2.VideoWriter('test.avi', cv2.VideoWriter_fourcc(*'MJPG'), fps, size)
# load the video
print(cap.isOpened())
fram_num = 0
while (cap.isOpened()):  # play the video by reading frame by frame
    ret, frame = cap.read()
    if ret == True:
        loop = 0
        while loop < 25:
            x = all_coordinates[fram_num, 3*loop]
            y = all_coordinates[fram_num, 3*loop + 1]
            frame = cv2.circle(frame, (int(x), int(y)), radius=3, color=(0, 0, 255), thickness=-1)
            loop = loop + 1
        result.write(frame)
        fram_num = fram_num +1
    else:
        break
cap.release()
cv2.destroyAllWindows()
{{< / highlight >}} 


The code above manages to do the work properly. We first load a video and get the various informations required about it. We also load the coordinates of the keypoints with the right function. For each frame of the video we draw the corresponding coordinates on the sequence, leaving us with the following result :

{{< videofig mp4="/oui.mp4" loop=true autoplay=true caption="Yeah, it works" >}}

### Task 2 & 3

As for task 2 and 3, I've studied the sample code provided on the cloud share and tried to understood how it worked. It was basically taking what we did with the 2D TXT but transposing it with all the notions that we had worked on with epipolar geometry. Unfortnuately I cannot give you some videos for you to see how it worked.