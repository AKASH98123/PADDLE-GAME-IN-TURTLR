# PADDLE-GAME-IN-TURTLR

import turtle
a=turtle.Turtle()
b=turtle.Screen()
b.title(" WELCOME TO PONG GAME")
b.bgcolor("black")
b.setup(800,600)
# THIS IS A TWO PLAYER GAME NAME AS A AND B 
playerAscore=0
playerBscore=0
# NOW CREATE A LEFT PADDLE WHICH WILL BE MOVING 
leftpaddle=turtle.Turtle()#we make a paddle as the tyrtle because we want vto move the paddle 
leftpaddle.speed(6)
leftpaddle.shape("square")
leftpaddle.color("blue")
leftpaddle.shapesize(6,1,5)
leftpaddle.up()
leftpaddle.goto(-350,0)
leftpaddle.down()


# NOW CREATE A RIGHTPADDLE WHICH WILL BE MOVING 
rightpaddle=turtle.Turtle()
rightpaddle.speed(6)
rightpaddle.shape("square")
rightpaddle.color("blue")
rightpaddle.shapesize(6,1,5)
rightpaddle.up()
rightpaddle.goto(350,0)
rightpaddle.down()


# NOW CREATE A BALL (NOT TWO WET BALLS)
ball=turtle.Turtle()
ball.shape("circle")
ball.speed(0)
ball.color("yellow")
# for i in range(10):
#     ball.up()
#     ball.fd(700)
#     ball.goto(0,0)
#     ball.bk(350)
#     ball.down()
ball.up()
ball.goto(5,5)
ballxdirection=5
ballydirection=5
# CREATE THE PEN FOR UPDATING THE SCORE
pen=turtle.Turtle()
pen.speed(6)
pen.color("white")
pen.up()
pen.hideturtle()
pen.goto(0,260)
pen.write("score",align="center",font=("Arial",24,"bold"))

# NOW WE ARE GOING TO MOVE OUR LEFTPADDLE IN UPWARD DIRECTION
def leftpaddleup():
    y=leftpaddle.ycor()  #RETURNS THE TURTLE'S Y COORDINATE WHERE IS THE TURTLE PRESENT 
    y=y+90
    leftpaddle.sety(y)#SET THE TURTLE Y COORDINATE KEEPING THE X COORDINATE SAME 

# NOW WE ARE GOING TO MOVE OUR RIGHTPADDLE IN DOWNWARD DIRECTION
def leftpaddledown():
    y=leftpaddle.ycor()  
    y=y-90
    leftpaddle.sety(y)

#NOW SIMILARLY FOR THE RIGHT PADDLE 
def rightpaddleup():
    y=rightpaddle.ycor()  
    y=y+90
    rightpaddle.sety(y)

def rightpaddledown():
    y=rightpaddle.ycor()  
    y=y-90
    rightpaddle.sety(y)

# ASSIGN THE KEY FOR PLAYING
b.listen()
b.onkeypress(leftpaddleup,'w')# w AND s are the key names 
b.onkeypress(leftpaddledown,'s')
b.onkeypress(rightpaddleup,'Up')
b.onkeypress(rightpaddledown,'Down')# Up AND Down ARE ALSO THE KEY NAMES 

# NOW MOVING THE BALL 
while True:
    b.update()
    ball.setx(ball.xcor()+ballxdirection)#HERE BALL IS MOVING IN THE X DIRECTION WITH SPEED THE 0.2 FRAME 
    ball.sety(ball.ycor()+ballydirection)

    #setting the border
    if ball.ycor()>290:
        ball.sety(290)
        ballydirection=ballydirection*-1
    if ball.ycor()<-290:
        ball.sety(-290)
        ballydirection=ballydirection*-1

    if ball.xcor()>390:#IF BALL NOT TOUCHING THE PADDLE 
        ball.goto(0,0)
        ballxdirection=ballxdirection
        playerAscore=playerAscore+1
        pen.clear()
        pen.write("Player A:{}    Player B:{} ".format(playerAscore,playerBscore),align="center",font=("Arial",24,"bold"))

    if ball.xcor()<-390:#IF BALL NOT TOUCHING THE PADDLE 
        ball.goto(0,0)
        ballxdirection=ballxdirection*-1
        playerAscore=playerAscore+1
        pen.clear()
        pen.write("Player A:{}    Player B:{} ".format(playerAscore,playerBscore),align="center",font=("Arial",24,"bold"))    

    #HANDLING THE COLLISION WITH THE PADDLE 
    if (ball.xcor()>340 and ball.xcor()<350) and (ball.ycor()<rightpaddle.ycor()+40 and ball.ycor()>rightpaddle.ycor()-40):
        ball.setx(340)
        ballxdirection=ballxdirection*-1#FOR INVERTING THE DIRECTION OF BALLL
    
    if (ball.xcor()<-340)and (ball.xcor()>-350)and (ball.ycor()<leftpaddle.ycor()+40 and ball.ycor()>leftpaddle.ycor()-40):
        ball.setx(-340)
        ballxdirection=ballxdirection*-1







