## Moving Link
<img src="https://github.com/Qiugu-He/20-React-App/blob/master/05-Moving_Link/MoveLink.png" alt="alt text" width="100%" height="100%">

This small app is primarily let me practiced react hooks: 
* <b>useState, useEffect, useRef</b>
* My summaries for React Hooks can visite my blog posts at: [Qiugu's Blog](http://143.110.221.115/)

### Main Rendering flow:
```javaScript
    //Ref variable
    const canvasRef = useRef(null);
    const linkDownRef = useRef(null);
    const linkUpRef = useRef(null);
    const linkRightRef = useRef(null);
    const linkLeftRef = useRef(null);

    // ......

    //set the height and width of canvas
    /*
        - this will only run when application get mounted, never re-run
        - act like componentdidmount 
    */
    useEffect(() => {
        const context = canvasRef.current.getContext('2d');
        context.canvas.height = window.innerHeight;
        context.canvas.width = window.innerWidth;
    }, []);

    //move the hero
    /* 
        - Run only if x or y changes, and 
        - componentdidupdate
    */
    useEffect(() => {
        const context = canvasRef.current.getContext('2d');
        
       //Make sure there are only one image appear, so dont have repeat image after each rendering
        context.clearRect(0, 0, window.innerWidth, window.innerHeight);

        let theLinkRef;
        if (direction === 'down') theLinkRef = linkDownRef;
        if (direction === 'up') theLinkRef = linkUpRef;
        if (direction === 'left') theLinkRef = linkLeftRef;
        if (direction === 'right') theLinkRef = linkRightRef;

        //draw the image
        context.drawImage(theLinkRef.current, x, y);
    }, [x, y]); // effectr be called when x, y changes

    //....
```

## How to Run :
- npm install<br>
- npm run
- npm build (For production)