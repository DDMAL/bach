Having now gone through several iterations- using the layers produced from the Classifying job as inputs into a pixel job with a new manuscript- I'm taking the tentative next step into introducing a new folio to the classifying job to see what layers it produces, correcting them, and sending them back around. 

Round and Iteration 1: 
Pixel has 4 ports: 
1) Image (color.png)
2) Layer 1 input
3) Layer 2 input
4) Layer 3 input
In the first round where there are no classified layers to connect, these will simply be present to establish the layers which will be labeled once Pixel opens. In your first iteration, you will need to include the background removal job. 

Pixel opens. In this case, there shouldn't be anything present, or everything should be highlighted- highlight/erase/correct per layer how you would like. If there is no text present, retain this third layer but send noice (document edges, shadows, etc.) to this layer. 

Once pixel is complete you will proceed to training. Ensure the number of layers you used in pixel matches the number of model outputs in training (probably 3 and 3, assuming music-staff-text). 

Models will be produced. Utilise these in classifying. Classifying will produce layers 1-3. These layers will be used on the next iteration through, assigning them to Layer X inputs in Pixel. The classifier layers are going to try and predict and correctly separate the layers of the image you used. 

This brings us back to the top, and at iteration 2. 

## Iteration 2
Back to pixel. Assign three layer # input ports, plus the image inport port for the color png image you are using. Assign the layers produced in the classifying stage to the relevant pixel input (e.g., layer 1 from classifying to pixel input layer 1, etc.). 

Run the job. It will open pixel, and will have tried to separate everything into the expected layers: it will have tried to use the data from your last round of pixel to correctly assign items. Most music notes should be the same color, the stafflines should all be mostly the same color, etc. Your job now is to correct the incorrect or spillover colors; I recommned making good use of the select tool which will allow you to cut or copy items from one layer and move them to another. This is particularly helpful for where a clutch of notes are highlighted as staff layer- simply select all of the relevant notes in the staff layer, ctrl-x, select/navigate to the notes layer, ctrl-c. The incorrectly highlighted items from the staff layer should now be the correct color for items in the notes layer. 

Once you've completed your corrections, proceed to training using this produced file and the ZIP file from the previous iteration. 

Note that Rodan currently does not have the memory to manage more than 2 ZIP files **possibly not even more than 1**, so you will only want to use your  most recent files. 

Once training is complete, feed these models into the classifying job- again make sure the number of model inputs matches the number of layer outputs in classifying. The classifying inputs will be the number of models you have produced plus the RGB image job. 

Run classifying. 

It will produce 3 more layers, which you will then feed back into pixel for iteration 3. 

## Iteration 3

See above steps- from iteration 3 on, however, it should be increasingly accurate at layer separation. A way to maneuver around this for increasing accuracy is to move your selected region around the page. 


Once your model is producing separated layers to your satisfaction, we'll move on to new images with Iteration 4. 

## Iteration 4+

Much of this will proceed as in Iteration2, with the exception that the image you include will now be a new folio image which the machine hasn't 'seen'. Utilise the most recent classifier models, and run the pixel job again. 

It will likely have done a decently good job, but qill require more detailed manual correction. Select small regions to start, and iterate through as many times as necessary to have consistently accurate layer separation. 


## Iteration 5 + 

Continue testing with new images until you can successfully upload a new manuscript image with minimal correction. 



----

Current status 2024-06-10

In 'iteration + training' workflow run, I utilised a newly produced pixel.js ZIP file from  `random bach`  with the classifyer-produced layers from the image `bach full`. It is now training using that ZIP file and the produced ZIp file from the last `bach full` training round where the layers were successfully accurately separated. 


----

Note to self 2024-06-10 ~20:00:00 
Once `iteration+ training 2024-06-10 19:41:22` finishes, use the produced models for another round of classification with `BaRa1`. Once that is complete, train a new model and then do a round of classification using `it+ classifying - random image test` using the new models and `BaRa2`. 

---
