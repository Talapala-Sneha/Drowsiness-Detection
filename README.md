   A system which predicts if the driver is drowsy or alert using the principles of Image Processing in order to avoid road accidents. 
   A live video retrieved from a webcam is fed into the module. The video is then sliced into a number of frames. The module checks for faces in each frame. 
   If too many faces or no faces are detected, it throws an error stating no face or too many faces detected.
   If a face is found, facial landmark detection algorithm of DLIB is applied. 
   This is used to detect and localize important regions of the face, including eyes, eyebrows, nose, ears, and mouth.
   Hence we can extract the specific facial structures required by determining the indexes of the particular required face parts. 
   As a result, with the co-ordinates of the eye regions, the eye regions can be extracted.
   Since, we require only the eye portions to determine whether the eye is closed or open, only the eye regions are extracted using facial landmark detection.
   Each eye is represented by six (x, y)-co-ordinates, starting at the left-corner of the eye and 
   the remaining five points are plotted clockwise around the remainder of the region.
The Eye Aspect Ratio (EAR)  is calculated using the formula - 
            
                                      ||P2-P6||+||P3-P5||  
              EAR  =      
                                     2||P1-P4||
 
Where p1, …, p6 are 2D facial landmark locations. 
The numerator of this equation computes the distance between the vertical eye landmarks while the denominator computes the distance between horizontal eye landmarks,
weighting the denominator appropriately since there is only one set of horizontal points but two sets of vertical points.
The eye aspect ratio is approximately constant while the eye is open, but will rapidly fall to zero when a blink occurs.
                      From the previous module, eye aspect ratio is determined. 
By experimenting, a threshold value for which the eye is open is found. If the eye aspect ratio falls below a fixed threshold, the number of frames for which the person has closed their eyes is automatically counted. If the number of frames the person has closed their eyes exceeds the number of a predefined variable, which denotes the number of consecutive frames an eye can be closed. When the value becomes higher, the drowsiness of the driver is detected. Then, he/she is declared as unfit to drive. Sometimes, the driver may blink and the module may detect that as drowsy. This can be avoided by setting the frame count as high. However, if the frame count is very high, detection may take a longer time and hence the accident cannot be prevented. Therefore, the frame count must be optimal.