# panel Log

To show panels in console log.
It not work on VSCode output and some anothers IDEs.

## Output

```
  Application         Version             Time Running        Load                                                                                  
  My App              1.0.0               0:00                COMPLETE                                                                              
----------------------------------------------------------------------------------------------
  Size                Length              Total               Money                                                                                 
  10                  5                   15                  $ 510.37                                                                              
----------------------------------------------------------------------------------------------
[ITEM 0] x{1 value: 3 
[ITEM 1] x{2 value: 3 
[ITEM 2] x{3 value: 3 
[ITEM 3] x{4 value: 3 
[ITEM 4] x{5 value: 3 
----------------------------------------------------------------------------------------------

```

# Install

To install using npm

```

npm i  panel-log

```

## Git repository

https://github.com/reytuty/panel-log


# Instantate 

```
var panelLog = require('panel-log') ;
    panelLog.appName = "My App";
    panelLog.appVersion = "1.0.0";
    panelLog.start() ;
```


# Example

```
var pannelLog = require('panel-log') ;
    pannelLog.appName = "My App";
    pannelLog.appVersion = "1.0.0";
    pannelLog.start() ;
    //you can pass real things
    setTimeout(pannelLog.setPercentComplete, 500, 0.2);
    setTimeout(pannelLog.setPercentComplete, 1000, 0.4);
    setTimeout(pannelLog.setPercentComplete, 1500, 0.6);
    setTimeout(pannelLog.setPercentComplete, 2000, 0.8);
    setTimeout(pannelLog.setPercentComplete, 2500, 1);
    //Your custom data
    pannelLog.onUpdate.add(()=>{
        //my list
        var myList = [{x:1, value:3},{x:2, value:3},{x:3, value:3},{x:4, value:3},{x:5, value:3}] ;
        //create a line
        var width = 20 ;
        var headers = new pannelLog.Line()
        .padding(2)
        //create a column
        .column('Size', width, [pannelLog.color.cyan])
        .column('Length', width, [pannelLog.color.cyan])
        .column('Total', width, [pannelLog.color.cyan])
        .column('Money', width, [pannelLog.color.cyan])
        .fill()
        .output();
        
        //another line withi values
        var line = new pannelLog.Line()
        .padding(2)
        .column(Math.floor(Math.random()*30), width)
        .column(myList.length, width)
        .column(15, width)
        .column("$ "+(Math.random()*20000).toFixed(2), width)
        .fill()
        .output();
        //You also can use default console.log and it will persist on screen 
        console.log("----------------------------------------------------------------------------------------------") ;
        for(var i in myList){
            var item = myList[i] ;
            console.log("[ITEM "+i+"] x{"+item.x+" value: "+item.value+" ");  
        }

    }) ;
```