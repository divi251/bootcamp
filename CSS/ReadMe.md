![enter image description here](https://actyv-bootcamp.s3.ap-south-1.amazonaws.com/banners/css.jpg)

Learn CSS in one look

# Why CSS ?
If you create a house then it will require to set the orientation, size, height, location and other appearing features of the rooms.
You will also require to decide that on which floor your room should be and what should be the color of the each wall.
So CSS is not only a painting thing it decides the orientation and all appearing design of the individual app elements like button, text box,  images and all the things you see in a app

# Can HTML not solve this problem
No, HTML is just like the skeleton of the house. You can just put rows of bricks(HTML) one after one but to align it in particular direction or to make it appear like small or tall or colourfull you need CSS
Without CSS the app will be like a pdf document having text in each new line
If you write list of things in new lines then you cannot make it to appear in a single line or vice versa but CSS will give you the power to play with the orientations, animation and colors.

# Basic Syntax

We write CSS by selecting the tag on which we are going to apply CSS. So as given in figure first one is a selector which is selecting h1 tag now inside the bracket we are setting values to properties of that tag. so code should look like : 

    h1 {
    color : "yellow";
    font-size: 11px;
    }

![enter image description here](https://static.javatpoint.com/csspages/images/css-syntax.png)


# Let us start

**After These 10 Concepts you will  be enough to mention CSS in your resume**


# 1 : BOX MODEL 
> (Let us understand how the "Briks" of a house behaves ) : 

 Building block of of your house are "Briks". Similarly Building block of the  what you see in app  HTML elements. As you know some bricks are having borders also and some bricks are having some texts inside the border. 

![enter image description here](https://www.scidev.net/objects_store/thumbnail/066681D5B3125FB74DF61747F58457D1.jpg)

 Distance between the border and the text is call padding. Now border is the ending no any material is available outside of the border of the briks. Now how much space it wants to take even after it is stable and fixed. Means if you are in you office the you create a distance between other employess to sit similary that outer space after the border is called margin![enter image description here](https://www.websitenero.com/application/assets/img/html-module/box-model.png )

Increase in padding  will increase the width and height because it will create space for inner text of the briks
Increasing the margin will not increase height and width but it will increase the sourounding space. So the bricks have lot of space get reserved for there outer surface


# 2 : Type Of Elements 
> (Let us understand  Type of Briks use to create a house)

**Block** Elements are those Elements which takes full width on screen. No any other tag can be put inside the block tag in the same line. As shown in the figure.
Example :  div, P, h1-h6,header, footer

**Inline** Elements are those elements that do not take full width. As shown in figure
Example: span, input, button.

![enter image description here](https://miro.medium.com/max/2800/1*AFeOAqXNJJdfYAjfXiJ9AQ.jpeg)



# 3 : Selectors
> (Let us decorate a brick but first know how to select the brick ) :
> 
Selectors are used to select the elements to aplly styles on those elements.We can select the elements in different ways as given below.

**ELEMENT SELECTOR**
The element selector selects HTML elements based on the element name.

    p {  
    color:  red;  
    }

In following the example all P elements will be selected and color will be get changed.


**ID SELECTOR**
The id selector uses the id attribute of an HTML element to select a specific element. The id of an element is unique within a page, so the id selector is used to select one unique element. It is denoted by using # symbol


    <p id = "paragraph1">this is paragraph</p>
    <p>this is paragraph</p>
     
     // Now style it

    #paragraph1 {  
    color:  red;  
    }

Paragraph 1 will be get selected  and color will be changed at red

**CLASS SELECTOR** 
The class selector selects HTML elements with a specific class attribute.

    <p id = "paragraph1">this is paragraph</p>
    <p class = "class1">this is paragraph</p>
    
    p.class1 {  
        color:  red;  
        }

To select elements with a specific class, write a period (.) character, followed by the class name.

**UNIVERSAL SELECTOR**
The universal selector (*) selects all HTML elements on the page.

    * {  
    text-align:  center;  
    color:  blue;  
    }

**GROUP SELECTOR**

The grouping selector selects all the HTML elements with the same style definitions. Look at the following CSS code (the h1, h2, and p elements have the same style definitions):

    h1, h2, p {  
    text-align:  center;  
    color:  red;  
    }

# 4: Sudo ELements & Sudo Classes 
>(Can you color a brick when it do something):

**SUDO CLASSES**
Sudo classes are basically selectors. By using it, we can apply styles on the perticular state of the elements. For example on hover, on click, on invalid etc. If an element is going to be clicked then we can change the color or different styles we can change. 

Have a look on the following GIF
![enter image description here](https://i.stack.imgur.com/M4fQT.gif)
When user is hovering different sections,then on hover the color is getting changed
Look at one more GIF

![enter image description here](https://i.stack.imgur.com/yXTK5.gif)

Sudo classes are written by writing `:` after selectors.
See the following CSS. It will change the background color when the mouse hovers the div tag

    div {  
      background-color:  Green;     // original color
    }
    
    div:hover {  
    background-color:  blue;       // color when mouse hovers
    }

there are lot of pseudo-classes we can use. Following are pseudo classes :
![enter image description here](http://ways2web.weebly.com/uploads/5/4/4/8/54485903/3112201_orig.png)

**SUDO ELEMENTS**
Basically, we can apply styles on whole elements but we have to apply style on different parts of the element or inside element then Sudo element can help Sudo elements are used to style the particular part of an element. For example, if we want to add some text before the elements or after the elements or if we want to style the first line of text or if we  are going to change the color of selected text then we  use pseudo-elements.
Sudo elements are denoted by `::` after the element or selected elements
Let just see and example :
We have to change the color of first letter of elements

    <div>This is paragraph</div>
    <div>This is paragraph</div>
    <div>This is paragraph</div>
    <div>This is paragraph</div>
    

Output :  This is sentence

Now let just apply styles
  
     div :: first-letter {
          color: red,
          font-size : 20px
        }

Output : 
![enter image description here](https://www.w3.org/wiki/images/e/ef/Css3_selectors_first-letter_A.png)

this is how sudo elements works.

Following are different pseudo elements we use in CSS :

![enter image description here](https://css-tricks.com/wp-content/uploads/2012/07/multiple-pseudo.png)

     ::after              // Insert something after the content of each element
     ::before             // Insert something before the content of each element
     ::first-line         // style the first line of elment
     ::first-letter       // style the first Letter of elment
     :: Selection         // style the the selection effects when user selects text
     

# 5: Height, Width, Margin, Padding
>  (Let just play with Margin padding height and width)

Before starting this you should have to be clear about box model which we have cleared in first topic . Now let just start 

**Height** :  By name we can get to know what is height attribute is doing in CSS. It sets the height of elements.

**Width** : By name we can get to know what is width attribute is doing in CSS. It sets the width of the elements.

> 💡  Pro Tip :

 do not use height every time. Use it when it require. See how height can be a lithal to UI if we use it wrong. See the following example.
For example : let suppose if we are giving a fix height  and width to the button element when our website was on its initial phase.If our website is now supporting different languages and  if we are going to show a website in different languages then this is possible that particular word will contain more letter in English but we have fixed our height and width. Since height and width are fixed so the text will ovwerflow from the box. UI changes as shown in figure

![enter image description here](https://i.stack.imgur.com/a990r.png)
So use padding for those things so text will be adjusted inside the box if text is increasing due to dynamic changes.

**Margin** :
Basicaly the area around the element is the margin. Margin decides that how much distance that elemnt should have to maintain from the other. I other element is maintaining there marginal distance then both margin will be get added and distance will be more.
Margin can be set in four directions Top, left, bottom, right.
this is how to apply margin:

    p {  
    margin-top:  25px;
    margin-right :  50px;
    margin-bottom :  75px ;
    margin-left : 100px;  
    }

you can apply margin to all side by using shorthand in one line : 

    p {  
    margin:  25px 50px 75px 100px;  
    }

you can apply margin to all side by equal distance using shorthand in one line : 

    p {  
    margin:  25px 50px    
    }
First one `25px` will be top and bottom margin
second 50px will be left and right margin

💡 Pro Tip : 
You can set the margin property to `auto` to horizontally center the element within its container.
he element will then take up the specified width, and the remaining space will be split equally between the left and right margins.

    div {  
      width:  800px;  
      margin:  auto;  
      border:  1px solid red;  
    }
![enter image description here](https://scccd.instructure.com/courses/25772/files/3364312/preview?verifier=ZZmGXSY9YPLSsw8zooyn2sgb2oJikYfXVQsVXQ0h)
see in folwing fig the div tag is one  who is containing the color full boxes by applying margin auto it place it self horizontaly center 

**Padding**:  Area between the text and the border is called padding. padding is used to maintain distance from border . Similary we put tables in room by keeping some distance from wall.
Padding can be set in four directions Top, left, bottom, right.
It is written as : 

    button : {
       background-color : "blue";
       padding : 10px, 15px, 10px, 15px    // top,right,bottom,left (clockwise)
    }
Now you can see that text inside button is taking 15px on lft and right as padding and 10 px for top and bottom

![enter image description here](https://miro.medium.com/max/1440/1*XRXIbVb8de4MFqKC9P9Yig.png)
Padding shorthands are also same as margin. 

# 6 : Position
 > (Let us set the position)
 
 If you have to set your element on perticular position then you have to know the positioning in CSS. Basicaly a element can move `Top` `Bottom` `Left`  `Right` from where it actually exists.
 But CSS ask for refrnce that from where you want to take the positioning happen . So these top bottom, left and write are used with respect to follwing positions : 
 
 1: Relative
 2: Absolute
 3: Sticky
 4: Fixed

 **Relative** :  If you are defining in css that it element should be `top: 20` and `left : 20`with position relative then it will shift by taking origin of that point where it is defined . You can see in picture on second row that green one is shifted by taking the origin where it was earlier.

code will  be like this : 

    {
     position: relative,
     top: 20;
     Left:20;
     background-color: green;
    }

**Absolute**: If you are defining in css that it element should be `top: 20` and `left : 20`with position absolute then it will shift by taking the window as origin. If you have defined `position :relative`  in parent container then it will take origin from parent one not from window. You can see in picture on third row that green one is shifted by taking the box container as origin, because in code the container was set as position relative . So position avsolute always search for  position relative to make it origin otherwise it will take window as origin


    Box-Container {
         position: relative,   // parent is relative
        }

    boxGreen {
         position: absolute,    // child is absolute, it have parent with relative
         top: 10;
         Left:10;
         background-color: green;
    }

![enter image description here](https://miro.medium.com/max/1226/1*pe9E2kzrX48Wwn_0wKklmw.png)
 
 **Fixed** : Position fixed is used if you want make an the element not to move even after scrolling as you can see in image that header is not moving even after scrolling

![enter image description here](https://blog.froont.com/content/images/2015/01/05-fixed-position-FROONT.gif)

 you can write the position sticky as follows : 
 

    div {  
        position:  fixed;  
        top:  0;  
        width:  300px;  
        border:  3px solid #73AD21;  
        }

# 7 : Units 
> (brick is bigger than girrafe or smaller then Ant)

If we have to tell the elements to take some height or width, then we have to tell that how much he have to increase his width. 
In css that unites can be: 

 1. cm : Centimeters
 2. px : Pixels
 3. % : Percentage
 4. em : Relative to the font-size of the element (2em means 2 times the size of the current font)
 5. rem: Relative to the font-size of the element (2em means 2 times the size of the root' element's font)
 6. Vh : 1% of the height of the viewport
 7. vw : 1% of the width of the viewport

# 8 : Float 
 > (Let the brick of your house to float)

Float will let the element float to the upside from its positon. It will shrink the space where it was and adjacent elements will get closed to each other .
Float can be left or right .
If we apply float left to element the it will float on left. If we apply right then it will flow on right as shown in figure.

![enter image description here](http://www.corelangs.com/css/box/img/float-right.png)


this is how it is written in css : 
 For box 1
 
    #box1 {
      float : left                 // it will let the element to float right
      background-color : "voilet";
      width: 50;
      Heigth: 50;
    }

 For box 2
 
    #box2 {
      float : right               // it will let the element to float right
      background-color : "voilet";
      width: 50;
      Heigth: 50;
    }

**Problem with float :**
Since element will be floating, it will float up from the original positon like something float in air on its same Y coordinate. So elements will be get shifted due to shrink in space down side floating element because that space need to be covered and can not be empty.
Ignore all the terms given in the following  fig. just focus on the boxes. You can see in the left figure that blue and yellow boxes are floating and div who is containing it, now get shrunk. Right side image is showing the structure before the float happened.

![enter image description here](https://i.stack.imgur.com/gYRqS.jpg)

So , to fix this . We use clearfix method. In clear-fix method we will apply style  `overflow : auto` in parent component and it will automatically set the parent element to the size as it was before as shown in follwing figure
![enter image description here](https://s3.amazonaws.com/fourthbit-blog/2013-11-27-essential-css-positioning-for-everyone/clearfix.png)

this is how to write clearfix  exactly :

  

    div {
       overflow: auto;       // clearfix
    }
            
    #box1 {
       float : left         // left
    }
    
    #box1 {
       float : right        //right
    }
