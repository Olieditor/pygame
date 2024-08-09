Pygame Front Page
=================

import pygame
import sys
from pygame.locals import *

# Initialiser Pygame
pygame.init()

# Définir les couleurs
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)

# Configurer la fenêtre du jeu
SCREEN_WIDTH = 800
SCREEN_HEIGHT = 600
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption("Nights at Plushy Pals")

# Charger les images des peluches
timoute_img = pygame.image.load('timoute.png')
pikane_img = pygame.image.load('pikane.png')

# Position initiale des peluches
timoute_pos = [100, 100]
pikane_pos = [600, 100]

# Vitesse des peluches
timoute_speed = [1, 0]
pikane_speed = [0, 1]

# Fonction principale du jeu
def game_loop():
    clock = pygame.time.Clock()

    while True:
        for event in pygame.event.get():
            if event.type == QUIT:
                pygame.quit()
                sys.exit()

        # Déplacer Timoute
        timoute_pos[0] += timoute_speed[0]
        if timoute_pos[0] > SCREEN_WIDTH or timoute_pos[0] < 0:
            timoute_speed[0] = -timoute_speed[0]

        # Déplacer Pikane
        pikane_pos[1] += pikane_speed[1]
        if pikane_pos[1] > SCREEN_HEIGHT or pikane_pos[1] < 0:
            pikane_speed[1] = -pikane_speed[1]

        # Afficher les éléments
        screen.fill(BLACK)
        screen.blit(timoute_img, timoute_pos)
        screen.blit(pikane_img, pikane_pos)

        pygame.display.update()
        clock.tick(60)

# Démarrer le jeu
game_loop()

