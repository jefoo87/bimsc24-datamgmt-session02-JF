<!-- the script is where the js code goes -->
<script>
import { ref } from "vue";
const doc = document.documentElement;

doc.style.fontFamily = "arial"

let input = document.createElement("input")
input.style.width = "100%"
input.style.height = "30%"
input.style.fontSize = "12pt"
sidebar.appendChild(input)


let submitButton = document.createElement("button")
sidebar.appendChild(submitButton)
submitButton.innerHTML = "Submit"
submitButton.style.fontSize = title.fontSize


let resetButton = document.createElement("button")
sidebar.appendChild(resetButton)
resetButton.innerHTML = "Reset Button"
resetButton.style.fontSize = title.fontSize



submitButton.addEventListener('click', doSomething)
resetButton.addEventListener('click',resetMain)

const main = document.querySelector("#main")

function getSpaces(text){
    startIndex = 0
    indices = []
    index = 0
    for(let i =0; i < text.length; i++){
        if(text[i] == " "){
        indices.push(i)
        }
    }
    console.log(indices)
    return indices
}


function insertMoo(text){
    textLength = text.length
    mooAmount = Math.ceil(text.length / 20)
    for(let j = 0; j < mooAmount; j++){
        spaceIndex = getSpaces(text)
        insertPoint = spaceIndex[Math.floor(Math.random()*spaceIndex.length)]
        text = text.slice(0,insertPoint) + " MOO!" + text.slice(insertPoint)
        mooAmount -= 1
    }
    console.log(text)
    return text
}

function doSomething() {
    let inputText = insertMoo(input.value)
    console.log(inputText)
    //create p element
    let para = document.createElement("p")
    //fill p element with text from bar
    para.innerHTML = inputText
    //append element to main
    main.appendChild(para)
    console.log("clicked submit")
}

function resetMain(){
    main.innerHTML = ""
}

</script>



<!-- the template is where the html code goes -->
<template>
   
   <div id="navbar" class="container">  
        <div id="title">Cow Transcriber</div>
        
        <div id="logo">
            <img src="./cow.jpg" alt="macad cow">

        </div>
        

    </div>

    <div id="flex">

        <div id="sidebar" class="container"> <h3>Input Text to be Transcribed by the Cows Here:</h3> <br><br> </div>

        <div id="main" class="container"> Transcribed Text: </div>
    </div>



</template>



<!-- style is where the css code goes -->
<style scoped>
html{
    
    background-color: rgb(59, 59, 59); 
    color: white;
}

body{

    margin:0;
}

div{

    /* put the borders in the inside of container */
    box-sizing: border-box;
}

img{

    height: 100%;
    width: auto;

}

#navbar{

    height: 50px;
    border-color: red;
    margin: auto;
    padding: 10px;
    background-color: black;
}

#flex{
    
    display: flex;
    height: calc(100vh - 50px);
}

#sidebar{
    
    width:30%;
    border-color: white;

}

#main{
    width:70%;
    background-image: url("CowTyping.png");
    background-size:contain;

}

#title{
    width: 70%;
    float:left;
    font-size: 20px;
    font-weight: bold;
}

#logo{
    width: 30%;
    height: 100%;
    float:right;
    text-align: right;

}

.container{

    padding: 30px;

}

</style>