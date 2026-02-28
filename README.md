

import turtle

artistic_drawing = turtle.Screen() 
artistic_drawing.bgcolor('light blue')

draw = turtle.Turtle()
draw.speed(0)

def draw_sunset_sky():
    sky = turtle.Turtle()
    sky.hideturtle()
    sky.speed(0)
    sky.penup()

    sky_layers = [
        (360, 240, "lightblue"),   
        (240, 140, "#FDBE7B"),   # peach
        (140, 60, "#FF9E6D"),    # light orange
        (60, -40, "#FF7B6B"),    # slamonish pink
        (-40, -180, "#C56FA8"),  # pink-violet
        (-180, -360, "#8C5AA8"), # twilightish purple
    ]
#add rectancles accross the screen filling in each colour of the sunset one at a time
    for top, bottom, color in sky_layers:
        sky.color(color)
        sky.goto(-500, top)
        sky.pendown()
        sky.begin_fill()
        sky.goto(500, top)
        sky.goto(500, bottom)
        sky.goto(-500, bottom)
        sky.goto(-500, top)
        sky.end_fill()
        sky.penup()

draw_sunset_sky()

#fuction to draw mountians
def draw_mountain(base_left, peak, base_right, body_color, shade_color):
    
    draw.color(body_color)
    draw.penup()
    draw.goto(base_left)
    draw.pendown()
    draw.begin_fill()
    draw.goto(peak)
    draw.goto(base_right)
    draw.goto(base_left)
    draw.end_fill()

 #outlines the mountains (used codex to help figure out how to do this)
    shade_split = ((peak[0] + base_right[0]) / 2, (peak[1] + base_right[1]) / 2)
    draw.color(shade_color)
    draw.begin_fill()
    draw.goto(peak)
    draw.goto(base_right)
    draw.goto(shade_split)
    draw.goto(peak)
    draw.end_fill()

draw_mountain((-420, -360), (-140, 20), (140, -360), "gray", "dim gray")
draw_mountain((-220, -360), (100, 70), (420, -360), "gray", "dim gray")



# cloud function
def circle(radius):
    draw.begin_fill()
    draw.circle(radius)
    draw.end_fill()

# clouds
draw.color("white")


# Individual locations for the cirlces that make up the left cloud
draw.penup()
draw.goto(-260, 160)
draw.pendown()
circle(45)

draw.penup()
draw.goto(-210, 200)
draw.pendown()
circle(60)

draw.penup()
draw.goto(-140, 180)
draw.pendown()
circle(50)

draw.penup()
draw.goto(-190, 150)
draw.pendown()
circle(55)

# Individual locations for the cirlces that make up the right cloud
draw.penup()
draw.goto(140, 160)
draw.pendown()
circle(45)

draw.penup()
draw.goto(190, 200)
draw.pendown()
circle(60)

draw.penup()
draw.goto(260, 180)
draw.pendown()
circle(50)

draw.penup()
draw.goto(210, 150)
draw.pendown()
circle(55)

# Sun 
sun_center = (-10, 180)
sun_radius = 85

# Sun Light/Glow 
for glow_radius, glow_color in [(130, "yellow"), (118, "gold"), (105, "orange")]:
    draw.penup()
    draw.goto(sun_center[0], sun_center[1] - glow_radius)
    draw.setheading(0)
    draw.color(glow_color)
    draw.pendown()
    draw.begin_fill()
    draw.circle(glow_radius)
    draw.end_fill()

draw.penup()
draw.goto(sun_center[0], sun_center[1] - sun_radius)
draw.setheading(0)
draw.color("orange")
draw.pendown()
draw.begin_fill()
draw.circle(sun_radius)
draw.end_fill()

#sun rays
draw.penup()
draw.goto(sun_center)
draw.setheading(0)
draw.pensize(4)
     
ray_length = 55  

for _ in range(16):
    draw.penup()
    draw.goto(sun_center)
    draw.forward(sun_radius)
    draw.pendown()
    draw.forward(ray_length)
    draw.penup()
    draw.goto(sun_center)
    draw.right(360/16)

draw.pensize(1)






artistic_drawing.mainloop()
