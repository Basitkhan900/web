<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
*{
    margin: 0;
    padding: 0;
    outline: 0;
    box-sizing: border-box;
}
body{
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background: #ebeef1;
}
.container{
    width:260px;
    background: #ebeef1;
    padding: 10px 15px 10px 15px;
    border-radius: 15px;
    box-shadow: 10px 10px 10px -1px rgba(10, 99, 169, 0.16),
    -10px -10px 10px -1px rgba(255, 255, 255, 0.70);

}
.heder{
    display: flex;
    justify-content:space-between;
    align-items: center;
}
.time{
    display: flex;
    align-items: center;
    gap: 5px;
}
.time span{
    font-size: 10px;
    font-weight: 500;
    color: #000;
}
.wifi i{
    font-size: 12px;
    color: #000;
}
.div{
    width: 40px;
    height: 5px;
    border-radius: 5px;
    background: #000;
    position: relative;
}
.div::after{
    content: '';
    position: absolute;
    width: 5px;
    height: 5px;
    background: #000;
    border-radius: 50%;
    top: 0;
    left: 110%;
}
.display{
    width: 100%;
    height: 60px;
    border: none;
    background: #ebeef1;
    box-shadow: 10px 10px 10px -1px rgba(10, 99, 169, 0.16),
                -10px -10px 10px -1px rgba(255, 255, 255, 0.70),
               inset 10px 10px 10px -1px rgba(10, 99, 169, 0.16),
              inset -10px -10px 10px -1px rgba(255, 255, 255, 0.70);
    font-size: 30px;
    font-weight: 400;
    text-align: right;
    padding-left: 10px;
    padding-right: 10px;
    border-radius: 10px;
    position: relative; 
    margin-top: 15px;
}
.display::after{
    content: '';
    position:absolute;
    width: 98%;
    height: 98%;
    top: 0;
    left: 0;
    background: #0068d1;
}
.buttons{
    display: flex;
    justify-content:center;
    align-items: center;
    gap:5px;
    flex-wrap: wrap;
    margin-top: 20px;
}
.buttons button{
    width: 40px;
    height: 40px;
    margin: 5px;
    border: none;
    border-radius: 5px;
    box-shadow: 10px 10px 10px -1px rgba(10, 99, 169, 0.16),
    -10px -10px 10px -1px rgba(255, 255, 255, 0.70);
    font-size: 18px;
    font-weight: 500;
    cursor: pointer;
}
.buttons button:active{
    transform: scale(0.9);
    background: #d9e4c8;
}
.oparator{
    color: #0068d1;
}
.buttom_button{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 30px;
    margin-top: 20px;
}
.buttom_button i{
    font-size: 14px;
    color: #676d72;
    cursor: pointer;
}
.buttom_button i:hover{
    transform: scale(0.9);
}
</style>
</head>

<body>
    <div class="container">
        <div class="heder">
            <div class="time"><span>08:12</span>
                <div class="wifi"><i class="fa-solid fa-wifi"></i></div>
            </div>
            <div class="div"></div>
            <div class="battary"><i class="fa-solid fa-battery-half"></i></div>
        </div>
        <input type="text" class="display">
        <div class="buttons">
            <button class="oparator" data-value="AC">AC</button>
            <button class="oparator" data-value="DEL">DEL</button>
            <button class="oparator" data-value="%">%</button>
            <button class="oparator" data-value="/">/</button>

            <button data-value="7">7</button>
            <button data-value="8">8</button>
            <button data-value="9">9</button>
            <button class="oparator" data-value="*">*</button>

            <button data-value="4">4</button>
            <button data-value="5">5</button>
            <button data-value="6">6</button>
            <button class="oparator" data-value="-">-</button>

            <button data-value="1">1</button>
            <button data-value="2">2</button>
            <button data-value="3">3</button>
            <button class="oparator" data-value="+">+</button>

            <button data-value="0">0</button>
            <button data-value="00">00</button>
            <button data-value=".">.</button>
            <button class="oparator" data-value="=">=</button>
        </div>
        <div class="buttom_button">
            <i class="fa-solid fa-chevron-left"></i>
            <i class="fa-regular fa-circle"></i>
            <i class="fa-regular fa-square"></i>

        </div>
    </div>
    <script>
const display = document.querySelector('.display')
 
 const buttons = document.querySelectorAll('button')
 console.log(buttons)

 const specialChars = [ "%", "*", "/", "-", "+", "="];
 let output = "";

 const calculate = (btnValue) =>{
    if(btnValue === "=" && output !== "") {
        output = eval(output.replace("%", "/100"));
    }
    else if( btnValue === "AC"){
        output = ""
    }
    else if( btnValue === "DEL"){
        output = output.toString().slice(0, -1);
    } else{
        if (output === "" && specialChars.includes(btnValue)) return;
        output += btnValue;
    }
    display.value = output;
 };

 buttons.forEach((button) => {
     button.addEventListener('click', e=> calculate(e.target.dataset.value));
 });
</script>
</body>
</html>
