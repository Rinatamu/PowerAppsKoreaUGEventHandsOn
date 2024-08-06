How to create Piano App on Power Apps.

===

## Reference Information.

This procedure manual was prepared by translating site into English.  

[Power Apps でピアノアプリを爆速で作る方法](https://jn.hateblo.jp/entry/2020/09/07/000000)    
> How to make piano apps with Power Apps in a blazing fast way!!
  
Wrote by **[Junichi Kodama](https://x.com/KodamaJn)**.


## First Completed Version.

We will now create such an application.

![](pasteimage/2024-08-06-20-23-19.png)

The range of notes that can be played by this application is one octave from C3 to C4.

![](pasteimage/2024-08-06-20-36-49.png)

## Advance preparation.

* Power Apps environment for free development.  
  ex. [Power Apps Developer Plan](https://www.microsoft.com/en-us/power-platform/products/power-apps/free?msockid=2ad762d298a164e03f9f76f1997365fa)

* Touch panel enabled device.  
ex. Tablet, SmartPhone  
Notice : Android is preferred because iOS has a delay in sound playback.

* Sound Files : [Download Link](https://bit.ly/3LJvnfA)  
   These sound files are customized version of sound file downloaded from "[Electronic Music Studios](https://theremin.music.uiowa.edu/MISpiano.html)" at the University of Iowa.  
Therefore, the copyright of the sound files belongs to the University of Iowa.

## 1. Sound Files Upload.

1. Open [Power Apps Designer](https://make.powerapps.com/).  
![](pasteimage/2024-08-06-22-00-11.png)

2. Click to "Create".  
![](pasteimage/2024-08-06-22-00-34.png)

3. Click to "Blank app".  
![](pasteimage/2024-08-06-22-04-57.png)

4. Click to Blank canvas app's "Create".  
![](pasteimage/2024-08-06-22-07-15.png)

5. Enter an appropriate name in the App name field, and choice to "tablet" on Format radiobox, Finaly click to "Create".  
![](pasteimage/2024-08-06-22-12-30.png)

6. Power Apps Designer is open.  
![](pasteimage/2024-08-06-22-14-23.png)

7. Click to "Media"  in the left pane.
![](pasteimage/2024-08-06-22-16-38.png)

8. Click to "Add Media" and then click to "Upload".
![](pasteimage/2024-08-06-22-18-47.png)

9. When the File Dialog opens, select all the downloaded Soundfiles and click to "open".
![](pasteimage/2024-08-06-22-23-18.png)

10. The selected sound file will be added in the Media menu.
![](pasteimage/2024-08-06-22-26-40.png)

## 2. Create first white piano keyboard.

1. Click to "Tree view"  in the left pane.
![](pasteimage/2024-08-06-22-36-52.png)

2. Click to "Insert" and then click to "Button".
![](pasteimage/2024-08-06-22-37-46.png)

3. Button is generated and moves to the upper left corner of the screen.  
The X and Y values of the position property should be 0.
![](pasteimage/2024-08-06-22-42-25.png)

4. Since we are creating a one-octave white key, enter the following expression for the Width property.  
    ```Javascript
    RoundDown(App.Width/8,0)
    ```
    ![](pasteimage/2024-08-06-22-46-55.png)

5. Enter the following expression for the Height property.
    ```Javascript
    App.Height
    ```
    ![](pasteimage/2024-08-06-22-59-17.png)

6. Click to the Color Fill Propaty, and then change color to White.
![](pasteimage/2024-08-06-23-01-43.png)  
![](pasteimage/2024-08-06-23-02-13.png)

7. Enter the following expression for the BorderColor property.
    ```Javascript
    Color.Black
    ```
![](pasteimage/2024-08-06-23-04-25.png)

8. Enter the following expression for the HoverFill property.
    ```Javascript
    ColorFade(Color.LightGray, 5%)
    ```
    ![](pasteimage/2024-08-06-23-07-53.png)


9. Click to "Insert" and then click to "Media" > "Audio".
![](pasteimage/2024-08-06-23-10-02.png)

10.  Audio Control is generated and moves to the upper left corner of the screen.  
The X and Y values of the position property should be 0.
![](pasteimage/2024-08-06-23-12-24.png)

11. Enter the following expression for the Width property.  
    ```Javascript
    RoundDown(App.Width/8,0)
    ```
    ![](pasteimage/2024-08-06-23-13-47.png)

12. Click to "Media" property, and select "01-C3".
![](pasteimage/2024-08-06-23-16-18.png)

13. Enter the following expression for the Start property.  
    ```Javascript
    Button1.Pressed
    ```
    ![](pasteimage/2024-08-06-23-18-36.png)

14. Enter the following expression for the Reset property.  
    ```Javascript
    !Button1.Pressed
    ```
> **Explanation Section**  
The audio control plays the specified media when the Start property
is set to True, the specified media is played. Therefore, by using the value of the Pressed property, which determines whether a button is pressed or not, the sound will be played when the key is pressed and will stop when the key is released. Also, setting the Reset property to True will return the media playback position to its initial value. Therefore, the Reset property is set to Pressed with the NOT symbol placed at the beginning.

15. From the Tree View, click the "Button1" menu and click "Reorder" > "Bring to front".
![](pasteimage/2024-08-06-23-36-51.png)

16.  From the Tree View, Shift+click the "Button1" and "Audio1".
![](pasteimage/2024-08-06-23-39-15.png)

17. click the menu and click to "Group".
![](pasteimage/2024-08-06-23-40-09.png)

18. "Button1" and "Audio1"are grouped together to form "Group1".
![](pasteimage/2024-08-06-23-42-22.png)

## 3. Copy and Paste of the white piano keyboards.

1. Select to "Group1" and Press key Ctrl+C.
![](pasteimage/2024-08-07-01-58-34.png)

2. Press Key Ctrl+V then Generate to "Group1_1"
![](pasteimage/2024-08-07-02-07-45.png)

3. Enter the following expression in the X property of "Group1_1".
    ```Javascript
    Self.Width
    ```
    ![](pasteimage/2024-08-07-02-13-13.png)

4. Expand "Group1_1" and select "Audio1_1".
![](pasteimage/2024-08-07-02-14-54.png)

5. Change the media property of "Audio1_1" to "03-D3". 
![](pasteimage/2024-08-07-02-17-47.png)

6. Repeat Ctrl+V 6 more times and change each parameter as shown in the table below.

    |Group Name|"X" property|"Media" Property|
    |:--|:--|:--|
    |Group1_2|```Self.Width*2```|```05-E3```|
    |Group1_3|```Self.Width*3```|```06-F3```|
    |Group1_4|```Self.Width*4```|```08-G3```|
    |Group1_5|```Self.Width*5```|```10-A3```|
    |Group1_6|```Self.Width*6```|```12-B3```|
    |Group1_7|```Self.Width*7```|```21-C4```|

    ![](pasteimage/2024-08-07-02-28-57.png)

## 4. Create first black piano keyboard.

1. Click to "Insert" and then click to "Button".
![](pasteimage/2024-08-06-22-37-46.png)

2. Button is generated.
![](pasteimage/2024-08-07-02-34-02.png)


3. Enter the following expression for the Width property.  
    ```Javascript
    RoundDown(App.Width/10,0)
    ```
    ![](pasteimage/2024-08-07-02-40-31.png)

4. Enter the following expression for the Height property.  
    ```Javascript
    RoundDown(App.Height/2,0)
    ```
    ![](pasteimage/2024-08-07-02-42-04.png)

5. Enter the X and Y properties as follows.  
    X : ```100```  
    Y : ```0```    
    ![](pasteimage/2024-08-07-02-46-02.png)

6. Click to the Color Fill Propaty, and then change color to Black.
![](pasteimage/2024-08-07-02-47-37.png)
![](pasteimage/2024-08-07-02-48-01.png)

7. Erase the value of the Text property
![](pasteimage/2024-08-07-02-49-32.png)

8. Enter the following expression for the HoverFill property.
    ```Javascript
    ColorFade(Color.White, -60%)
    ```
    ![](pasteimage/2024-08-07-02-51-28.png)


9. Click to "Insert" and then click to "Media" > "Audio".
![](pasteimage/2024-08-06-23-10-02.png)

10.  Audio Control is generated and enter the X and Y properties as follows.  
    X : ```Button2.X```  
    Y : ```Button2.Y```
    ![](pasteimage/2024-08-07-02-57-30.png)

11. Enter the following expression for the Width property.  
    ```Javascript
    Button2.width
    ```
    ![](pasteimage/2024-08-07-03-01-14.png)

12. Click to "Media" property, and select "02-Db3".
![](pasteimage/2024-08-07-03-03-35.png)

13. Enter the following expression for the Start property.  
    ```Javascript
    Button2.Pressed
    ```
    ![](pasteimage/2024-08-07-03-04-51.png)

14. Enter the following expression for the Reset property.  
    ```Javascript
    !Button2.Pressed
    ```
    ![](pasteimage/2024-08-07-03-05-46.png)

15. From the Tree View, click the "Button2" menu and click "Reorder" > "Bring to front".
![](pasteimage/2024-08-07-03-06-44.png)

1.   From the Tree View, Shift+click the "Button2" and "Audio2".
![](pasteimage/2024-08-07-03-07-36.png)

2.  click the menu and click to "Group".
![](pasteimage/2024-08-06-23-40-09.png)

1.  "Button2" and "Audio2"are grouped together to form "Group2".
![](pasteimage/2024-08-07-03-08-08.png)

## 5. Copy and Paste of the black piano keyboards.

1. Select to "Group2" and Press key Ctrl+C.
![](pasteimage/2024-08-07-03-09-42.png)

2. Repeat Ctrl+V 4 more times and change each parameter as shown in the table below.

    |Group Name|"X" property|"Media" Property|
    |:--|:--|:--|
    |Group2_1|```272```|```04-Eb3```|
    |Group2_2|```612```|```07-Gb3```|
    |Group2_3|```782```|```09-Ab3```|
    |Group2_4|```952```|```11-Bb3```|

    ![](pasteimage/2024-08-07-02-28-57.png)

3. The piano application is now complete.  
Let's try it out!