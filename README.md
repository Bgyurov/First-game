int x=400;   //Променливи за топчето
int y=300;
int w=50;
int speedX=7; //Променливи за скоростта на топчето
int speedY=5;
int paddleX=50; //Променливи за едната платформа
int paddleY=50;
int paddleW=30;
int paddleH=100;
int paddleS=5;   //Скоростта на платформата
int paddleY1=100;  //Променливи за втората платформа 
int paddleX1 = 720;
int score = 0;  //Променливи за резултат
int score2 = 0;

void setup(){
  size(800,600);  //Размери на екрана

}

void draw(){
  background(#98FF24);  //фон
  stroke(255);
  line(400,30,400,700);  //Полето
  fill(255);
  ellipse(400,290,200,180);
  fill(0);
  strokeWeight(2);
  ellipse(x,y,w,w);  //Топчето
  fill(#DB2D1D);
  rect(paddleX1,paddleY1,paddleW,paddleH);  //Първата платформа
  fill(#3911F2);
  rect(paddleX, paddleY, paddleW, paddleH); //Втората платформа
  fill(#0337FF);
 strokeWeight(2);

  
  
  
   x += speedX;
    y += speedY;
   if(x > paddleX && x < paddleX + paddleW && y > paddleY && y < paddleY + paddleH){
     speedX *= -1 ;
   }
   if(x > paddleX1 && x < paddleX1 + paddleW && y > paddleY && y < paddleY1 + paddleH){
     speedX *= -1;
   }
   if(x > width || x < -1){
     speedX *= -1;
   }
   if(y > height || y < -1){
     speedY *= -1;
   }
   
   
   fill(#FF8E03);
   
    if(keyPressed && key == 'w'){
     paddleY = paddleY - paddleS;
   }
   if(keyPressed && key == 's'){
     paddleY = paddleY + paddleS;
   }

   
   if(keyPressed && keyCode == UP){
     paddleY1 = paddleY1 - paddleS;
   }
   if(keyPressed && keyCode ==DOWN){
     paddleY1 = paddleY1 + paddleS;
   }


fill(255);                  //ТЕКСТ "UKTC"
rect(150,0,180,50);
textSize(42);
fill(0,0,255);
text("UKTC-"+score,150,50);

fill(255);                 //ТЕКСТ "GPCHE"
rect(500,0,195,50);
textSize(42);
fill(255,0,0);
text(score2+"-GPCHE",500,50);


if(x>width){     //Резултат "UKTC"
  score++;
  x=600;
  y=400;
}
 if(x<0){      //Резултат "GPCHE"
   score2++;
   x=600;
   y=400;
 }

if(score>=10){    // Ака UKTC стане 10 играта свършва
  background(255);
  textSize(30);
  fill(#0738F5);
  text("UKTC WINS",300,50);
  textSize(30);
  text("Click'R'to make a rematch",200,100);
}
if(score2>=10){   // Ака GPCHE стане 10 играта свършва
  background(255);
  textSize(30);
  fill(255,0,0);
  text("GPCHE WINS",300,50);
   textSize(30);
  text("Click'R'to make a rematch",200,100);
}
if(keyPressed&& key=='r'){  // Когато натиснеш копчето 'r' играта започва отново 
  score=0;
  score2=0;

}
}
