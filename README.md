# loag пинг понг, запуск через vs code, язык Python. Игра на двоих.

from pygame import *

class GameSprite(sprite.Sprite):
    def __init__(self, i_image, x, y, size_x, size_y, speed):
        self.image = transform.scale(image.load(i_image), (size_x, size_y))
        self.speed = speed
        self.rect = self.image.get_rect()
        self.rect.x = x
        self.rect.y = y
    def reset(self):
        window.blit(self.image, (self.rect.x, self.rect.y))

class Player(GameSprite):
    def update(self):
        keys = key.get_pressed()
        if keys[K_w] and self.rect.y > 5:
            self.rect.y -= self.speed
        if keys[K_s] and self.rect.y < 420:
            self.rect.y += self.speed

win_width = 700
win_height = 500
window = display.set_mode((win_width, win_height))
window = display.set_mode((700,700))
back = (0, 0, 0)
clock = time.Clock()
racket1 = Player('wall.png', 30, 200, 50, 150, 4)
racket2 = Player('wall.png', win_width - 30, 200, 50, 150, 4)
ball = GameSprite('mch.png', 200, 200, 50, 50, 4)
racket1 = Player('wall.png', win_width - 80, 200, 50, 150,)
finish = False
game = True
while game:
    for e in event.get():
        if e.type == QUIT:
            game = False
    if not finish:
        window.fill(back)
        ball.reset()
        racket1.update_a()
        racket1.reset()
        racket2.update_b()
        racket2.reset()
    display.update()
    clock.tick(60)
    








        

