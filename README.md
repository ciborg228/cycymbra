# cycymbra
import pygame

if __name__ == '__main__':
    global pos
    pygame.init()

    width, height = list(map(int, input().split()))
    size = width, height
    screen = pygame.display.set_mode(size)

    running = True
    fps = 0
    fps2 = 1
    clock = pygame.time.Clock()
    while running:
        screen.fill((0, 0, 255))
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False
            if event.type == pygame.MOUSEBUTTONDOWN:
                pos = event.pos
                fps = 0
                fps2 = 0
        while fps2 != 1:
            pygame.draw.circle(screen, (255, 255, 0), pos, fps)
            pygame.display.flip()
            fps += 10
            clock.tick(30)
            for event in pygame.event.get():
                if event.type == pygame.QUIT:
                    running = False
                    fps2 = 1
                if event.type == pygame.MOUSEBUTTONDOWN:
                    screen.fill((0, 0, 255))
                    pygame.display.flip()
                    pos = event.pos
                    fps = 0
    pygame.quit()
