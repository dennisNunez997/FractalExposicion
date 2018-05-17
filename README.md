# FractalExposicion
exposicion
import turtle
print("a) Triángulo de Sierpiński ")
print("b) curva de Koch")
opcion = input("seleccione una opcion: ")

if (opcion == 'a'): 
    PROGNAME = 'Sierpinski Triangle'
    #Credits: This code was written by editing the code from http://www.lpb-riannetrujillo.com/blog/python-fractal/

    myPen = turtle.Turtle()
    myPen.ht()
    myPen.speed(5)
    myPen.pencolor('orange')

    points = [[-175,-125],[0,175],[175,-125]] #size of triangle

    def getMid(p1,p2):
        return ( (p1[0]+p2[0]) / 2, (p1[1] + p2[1]) / 2) #find midpoint

    def triangle(points,depth):

        myPen.up()
        myPen.goto(points[0][0],points[0][1])
        myPen.down()
        myPen.goto(points[1][0],points[1][1])
        myPen.goto(points[2][0],points[2][1])
        myPen.goto(points[0][0],points[0][1])

        if depth>0:
            triangle([points[0],
                        getMid(points[0], points[1]),
                        getMid(points[0], points[2])],
                   depth-1)
            triangle([points[1],
                        getMid(points[0], points[1]),
                        getMid(points[1], points[2])],
                   depth-1)
            triangle([points[2],
                         getMid(points[2], points[1]),
                         getMid(points[0], points[2])],
                   depth-1)


    triangle(points,4)
elif (opcion == 'b'): 
    def genera_koch(level,l):
        if level==0:
                turtle.forward(l)
        else:
                genera_koch(level-1,l/3)
                turtle.left(60)
                genera_koch(level-1,l/3)
                turtle.left(-120)
                genera_koch(level-1,l/3)
                turtle.left(60)
                genera_koch(level-1,l/3)
    turtle.setup(width=800,height=600,startx=400,starty=300)
    turtle.up()
    turtle.backward(250) # punto de referencia (hacia atrás)
    turtle.down()
    turtle.degrees() # grados
    turtle.tracer(1) # trazado
    genera_koch(4,400) # n sera el numero de veces q se repetira
    turtle.getscreen()._root.mainloop()

