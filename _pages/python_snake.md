---
layout: single
title: Un serpent en Python !
permalink: /divers/python_snake.html
toc: true
toc_sticky: true
toc_label: "Au menu"
toc_levels: 1
toc_icon: "infinity"

---

Le déroulé de ce projet est très largement inspirée de cette <a href="https://www.edureka.co/blog/snake-game-with-pygame/">page</a>.

<br/>

Les différentes fonctions du module Pygame qui seront utilisées sont listées ci-dessous avec leur documentation.
<table>
  <tr>
    <th>Fonction</th>
    <th>Documentation</th>
  </tr>
  <tr>
    <td>init()</td>
    <td>Initialise tous les modules importés par Pygame (renvoie un tuple indiquant les succès/échecs de ces initialisations)</td>
  </tr>
  <tr>
    <td>display.set_mode()</td>
    <td>Prend en argument un tuple (longueur, largeur) et crée l'écran du jeu.</td>
  </tr>
  <tr>
    <td>display.update()</td>
    <td>Rafraîchit l'écran du jeu.</td>
  </tr>
  <tr>
    <td>quit()</td>
    <td>Réinitialise les modules lors de l'arrêt du jeu.</td>
  </tr>
  <tr>
    <td>display.set_caption()</td>
    <td>Définit le titre en haut de l'écran de jeu.</td>
  </tr>
  <tr>
    <td>event.get()</td>
    <td>Renvoie la liste de tous les événements et les supprime de la file.</td>
  </tr>
  <tr>
    <td>Surface.fill()</td>
    <td>Remplit la surface d'une couleur uniforme.</td>
  </tr>
  <tr>
    <td>time.Clock()</td>
    <td>Crée un objet qui permet de suivre l'évolution du temps.font</td>
  </tr>
  <tr>
    <td>font.SysFont()</td>
    <td>Transforme une fonte du système en fonte de Pygame.</td>
  </tr>
</table>

Le caractère <em>#</em> permet d'écrire des commentaires qui ne seront pas exécutés. Lors de l'introduction de nouvelles fonctions, nous les commenterons pour expliciter leur utilité. Il est très important de commenter TOUT le code.

<h1 id="Ecran">
  Création de l'écran
</h1>
Pour créer l'écran de jeu avec Pygame, il suffit d'utiliser la fonction <em>display.set_mode()</em> en précisant la taille de l'écran. Les méthodes <em>init()</em> et <em>quit()</em> permettent de remettre à zéro les modules au début et à la fin du jeu. La méthode <em>update()</em> rafraîchit l'écran avec les nouvelles modifications.
<pre id="01-serpent_init">
import pygame # Importe le module
pygame.init() # Initialise les fonctions pygame
dis = pygame.display.set_mode((400, 300)) # Cree l ecran en precisant ses dimensions
pygame.display.update() # Rafraichit l ecran
pygame.quit() # Remet à zero toutes les fonctions
quit() # Quitte Python
</pre>

Lors du lancement de ce code, l'écran apparaît et se referme immédiatement. Pour éviter ceci, nous allons utiliser une boucle conditionnelle qui tourne tant que le jeu n'est pas terminé. Nous ajoutons également un titre à notre fenêtre.
<pre id="02-serpent_ecran">
import pygame
pygame.init()
dis = pygame.display.set_mode((400, 300))
pygame.display.update()
pygame.display.set_caption("Jeu du serpent") # Ajout d un titre
game_over = False # Vaut False tant que le jeu n est pas termine
while not game_over:
    for event in pygame.event.get():
        print(event) # Affiche tous les evenements
pygame.quit()
quit()
</pre>

Quand on lance ce script, il ne s'arrête jamais et affiche tous les événements qui ont lieu. Nous allons maintenant spécifier au programme de quitter quand on clique sur le bouton fermer (en haut à droite de la fenêtre). Pour faire ceci, Pygame possède un événement appelé <em>QUIT</em> :
<pre id="03-serpent_quit">
import pygame
pygame.init()

dis = pygame.display.set_mode((400, 300))
pygame.display.update()
pygame.display.set_caption("Jeu du serpent")
game_over = False # Vaut False tant que le jeu n est pas termine
while not game_over:
    for event in pygame.event.get():
        if event.type == pygame.QUIT: # Detection du clic
            game_over = True
pygame.quit()
quit()
</pre>

<h2>
  Exercices
</h2>
<ol>
  <li>Modifier la taille de l'écran.</li>
  <li>Modifier le titre de l'écran.</li>
</ol>

<h1 id="Serpent">
  Création de la tête du serpent
</h1>
Pour créer le serpent, on commence par définir quelques couleurs. Les couleurs sont définies dans le système RGB (Red/Green/Blue) en précisant les proportions de rouge/vert/bleu qu'elles possèdent. Le noir correspond au cas où 3 composantes sont à 0 ; le blanc à celui où les 3 composantes sont à 255. Le serpent sera défini à l'aide de rectangles. Dans Pygame, pour définir un rectangle, on utilise la fonction <em>draw.rect()</em> pour laquelle on précise la couleur et la taille. On stocke également les tailles de l'écran dans des variables pour pouvoir les modifier plus facilement.
<pre id="04-serpent_rectangle">
import pygame
pygame.init()

dis_width, dis_height = 800, 600 # Dimensions de l ecran

# Definition de couleurs
blue = (0, 0, 255)
red = (255, 0, 0)

dis = pygame.display.set_mode((dis_width, dis_height))

pygame.display.set_caption("Jeu du serpent")
game_over = False
while not game_over:
    dis.fill(red) # Couleur de fond en rouge
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game_over = True
	# Creation d un rectangle bleu
    pygame.draw.rect(dis, blue, [200, 150, 10, 10])
    pygame.display.update()
	
pygame.quit()
quit()
</pre>

<h2>
  Exercices
</h2>
<ol>
  <li>Modifier les dimensions de l'écran en modifiant le contenu des variables.</li>
  <li>Définir les couleurs vert et jaune.</li>
  <li>Modifier la couleur du fond de l'écran.</li>
  <li>Modifier la couleur du rectangle.</li>
  <li>En modifiant les valeurs 10/10, modifier la taille du rectangle.</li>
  <li>En modifiant les valeurs 200/150, modifier la posiion du rectangle</li>
  <li>En utilisant les variables <em>dis_width</em> et <em>dis_heigh</em> ainsi que la division <em>/</em>, créer un rectangle dont les longueurs et largeurs sont les moitiés de celles de l'écran</li>
</ol>


<h1 id="Deplacement">
  Déplacer la tête du serpent
</h1>
Pour faire bouger la tête du serpent, nous avons besoins d'utiliser les événements générés par les touches du clavier. Nous utiliserons ici <em>K_UP</em> (flèche vers le haut), <em>K_DOWN</em> (flèche vers le bas), <em>K_LEFT</em> (flèche vers la gauche et <em>K_RIGHT</em> (flèche vers la droite). Les variables <em>x1_change</em> et <em>y1_change</em> permettent d'enregistrer les modifications à effectuer sur la position du serpent.
<pre id="05-serpent_deplacement">
import pygame
pygame.init()

dis_width, dis_height = 800, 600

white = (255, 255, 255)
black = (0, 0, 0)
red = (255, 0, 0)

dis = pygame.display.set_mode((dis_width, dis_height))
pygame.display.set_caption("Jeu du serpent")

game_over = False
clock = pygame.time.Clock() # Recupere l heure

x1, y1 = 300, 300 # Position initiale du serpent 
x1_change, y1_change = 0, 0
 
while not game_over:
    for event in pygame.event.get():
        # Detection de l evenement
        if event.type == pygame.QUIT:
            game_over = True
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_LEFT:
                x1_change, y1_change = -10, 0
            elif event.key == pygame.K_RIGHT:
                x1_change, y1_change = 10, 0
            elif event.key == pygame.K_UP:
                x1_change, y1_change = 0, -10
            elif event.key == pygame.K_DOWN:
                x1_change, y1_change = 0, 10

    # Mise a jour de la position du serpent
    x1, y1 = x1 + x1_change, y1 + y1_change

    dis.fill(white)
    pygame.draw.rect(dis, black, [x1, y1, 10, 10])
 
    pygame.display.update()
 
    # Limite les rafraichissements de l ecran par seconde
    clock.tick(15)
 
pygame.quit()
quit()
o</pre>

<h2>
  Exercices
</h2>
<ol>
  <li>Modifier les couleurs du fond, du serpent.</li>
  <li>Modifier le titre de l'écran.</li>
  <li>Faire déplacer le serpent vers le bas quand on appuie sur la flèche vers le haut et vers le haut lorsqu'on appuie sur la flèche vers le bas !</li>
  <li>En modifiant l'argument de <em>tick</em>, faire se déplacer le serpent plus vite puis plus lentement.</li>
  <li>Faire s'arrêter le serpent lorsqu'on appuie sur la barre d'espace (<em>K_SPACE</em>).</li>
  <li>Au lancement du jeu, faire en sorte que le serpent se trouve au centre de l'écran.</li>
</ol>

<h1 id="Fin du jeu">
  Game over et frontières
</h1>

Nous allons modifier le code pour que, lorsque le serpent touche l'un des bords de l'écran, le jeu se termine. Pour programmer cette fonctionnalité, on utilise une conditionnelle <em>if</em> : lorsque les coordonnées du serpent sont en dehors de l'écran, le jeu termine. Un message s'affiche alors indiquant que le jeu est terminé.
<pre id="06-serpent_frontieres">
import pygame
import time # Module pour gérer le temps
pygame.init()

dis_width, dis_height = 800, 600

white = (255, 255, 255)
black = (0, 0, 0)
red = (255, 0, 0)

dis = pygame.display.set_mode((dis_width, dis_height))
pygame.display.set_caption("Jeu du serpent")
 
game_over = False

x1, y1 = dis_width/2, dis_height/2
snake_block = 10 # Taille de la tete du serpent
snake_speed = 15 # Rapidite du serpent
x1_change, y1_change = 0, 0

clock = pygame.time.Clock()

font_style = pygame.font.SysFont(None, 50) # Choix de la fonte

def message(msg, color):
    """msg : chaine de caracter
    color : couleur
    Affiche le message msg en couleur color"""
    mesg = font_style.render(msg, True, color)
    # Position et affichage du message
    dis.blit(mesg, [dis_width/2, dis_height/2])


while not game_over:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game_over = True
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_LEFT:
                x1_change, y1_change = -snake_block, 0
            elif event.key == pygame.K_RIGHT:
                x1_change, y1_change = snake_block, 0
            elif event.key == pygame.K_UP:
                x1_change, y1_change = 0, -snake_block
            elif event.key == pygame.K_DOWN:
                x1_change, y1_change = 0, snake_block
            elif event.key == pygame.K_SPACE:
                x1_change, y1_change = 0, 0

    # Sortie de l ecran
    if x1 >= dis_width or x1 < 0 or y1 >= dis_height or y1 < 0:
        game_over = True

    x1, y1 = x1 + x1_change, y1 + y1_change

    dis.fill(white)

    pygame.draw.rect(dis, black, [x1, y1, snake_block, snake_block])
 
    pygame.display.update()
 
    clock.tick(snake_speed)
 
# Message de fin de jeu
message("Vous avez perdu", red)
pygame.display.update()
time.sleep(2)
							     
pygame.quit()
quit()
</pre>


<h2>
  Exercices
</h2>
<ol>
  <li>Modifier le contenu du message affiché.</li>
  <li>Modifier la couleur du message affiché.</li>
  <li>Modifier le code pour que le serpent revienne par la gauche s'il touche le mur de droite sans que le jeu se termine.</li>
</ol>


<h1 id="Nourriture">
  Ajout de la nourriture
</h1>
Nous allons maintenant ajouter la nourriture. La nourriture sera disposée aléatoirement sur l'écran. À chaque fois que le serpent mange, on affiche le message MIAM!!. On ajoute également, lorsque le joueur perd, la possibilité soit de quitter le jeu, soit de rejouer.

<pre id="07-serpent_nourriture">
import pygame
import time
import random # Gestion des nombres aleatoires

pygame.init()

dis_width, dis_height = 800, 600

white = (255, 255, 255)
black = (0, 0, 0)
red = (255, 0, 0)
blue = (0, 0, 225)

dis = pygame.display.set_mode((dis_width, dis_height))
pygame.display.set_caption("Jeu du serpent")

snake_block = 10
snake_speed = 15

clock = pygame.time.Clock()

font_style = pygame.font.SysFont(None, 30)

def message(msg, color):
    """msg : chaine de caracter
    color : couleur
    Affiche le message msg en couleur color"""
    mesg = font_style.render(msg, True, color)
    # Recupere la taille du rectangle du texte
    text_rect = mesg.get_rect(center=(dis_width/2, dis_height/2))
    # Positionne et affiche le texte
    dis.blit(mesg, text_rect)

def gameLoop(): 
    game_over = False # Vaut False tant que le jeu n est pas terminé
    game_close = False # Vaut False tant qu on ne termine pas le jeu

    x1, y1 = dis_width/2, dis_height/2
    x1_change, y1_change = 0, 0

    # Position de la nourriture
    foodx = round(random.randrange(0, dis_width - snake_block)/10)*10
    foody = round(random.randrange(0, dis_height - snake_block)/10)*10

    while not game_over:
        while game_close:
            dis.fill(white)
            message("Vous avez perdu ! Cliquer sur Q pour quitter et N pour jouer une nouvelle partie", red)
            pygame.display.update()
            for event in pygame.event.get():
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_q:
                        game_over = True
                        game_close = False
                    if event.key == pygame.K_n:
                        gameLoop()

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                game_over = True
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    x1_change, y1_change = -snake_block, 0
                elif event.key == pygame.K_RIGHT:
                    x1_change, y1_change = snake_block, 0
                elif event.key == pygame.K_UP:
                    x1_change, y1_change = 0, -snake_block
                elif event.key == pygame.K_DOWN:
                    x1_change, y1_change = 0, snake_block
                elif event.key == pygame.K_SPACE:
                    x1_change, y1_change = 0, 0

        # Gestion torique de l ecran
        x1, y1 = (x1 + x1_change) % dis_width, (y1 + y1_change) % dis_height

        dis.fill(white)

        pygame.draw.rect(dis, black, [x1, y1, snake_block, snake_block])

        # Position de la nourriture serpent
        pygame.draw.rect(dis, blue, [foodx, foody, snake_block, snake_block])

        pygame.display.update()

        # Serpent mange la nourriture
        if x1 == foodx and y1 == foody:
            message("Miam!!", red)
            pygame.display.update()
            # Position de la nourriture
            foodx = round(random.randrange(0, dis_width - snake_block)/10)*10
            foody = round(random.randrange(0, dis_height - snake_block)/10)*10
            time.sleep(5) # Temps d affichage du message

        clock.tick(snake_speed)
							     
    pygame.quit()
    quit()

gameLoop()
</pre>

<h2>
  Exercices
</h2>
<ol>
  <li>Modifier les touches qui permettent de quitter et de rejouer</li>
  <li>Modifier le message MIAM!</li>
  <li>Modifier le temps d'affichage du message MIAM!</li>
</ol>

<h1 id="Taille">
Augmenter la taille du serpent
</h1>

Dans le code suivant, la taille du serpent augmente quand il mange de la nourriture. On modifie également le code pour que le jeu termine si le serpent rencontre une partie de son corps. Les différents éléments du corps du serpent sont stockés dans une liste.
<pre id="08-serpent_allongement">
import pygame
import time
import random

pygame.init()

dis_width, dis_height = 800, 600
snake_block = 10
snake_speed = 15

white = (255, 255, 255)
yellow = (255, 255, 102)
black = (0, 0, 0)
red = (255, 0, 0)
green = (0, 255, 0)
blue = (0, 0, 225)

dis = pygame.display.set_mode((dis_width, dis_height))
pygame.display.set_caption("Jeu du serpent")

clock = pygame.time.Clock()

font_style = pygame.font.SysFont(None, 25)

def message(msg, color):
    """msg : chaine de caracter
    color : couleur
    Affiche le message msg en couleur color"""
    mesg = font_style.render(msg, True, color)
    text_rect = mesg.get_rect(center=(dis_width/2, dis_height/2))
    dis.blit(mesg, text_rect)

def our_snake(snake_block, snake_list):
    """snake_block : taille du serpent
    snake_list : positions du corps du serpent
    dessine le serpent sur l ecran"""
    for i in range(0, len(snake_list)):
        x, y = snake_list[i]
        pygame.draw.rect(dis, black, [x, y, snake_block, snake_block])

def gameLoop():
    game_over = False
    game_close = False

    x1, y1 = dis_width/2, dis_height/2
    x1_change, y1_change = 0, 0

    # Definition du serpent
    snake_list = []
    length_of_snake = 1

    foodx = round(random.randrange(0, dis_width - snake_block)/10)*10
    foody = round(random.randrange(0, dis_height - snake_block)/10)*10

    while not game_over:
        while game_close:
            dis.fill(blue)
            message("Vous avez perdu ! Taper sur 'q' pour quitter et 'n' pour jouer une nouvelle partie", red)
            pygame.display.update()
            for event in pygame.event.get():
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_q:
                        game_over = True
                        game_close = False
                    elif event.key == pygame.K_n:
                        gameLoop()

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                game_over = True
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    x1_change, y1_change = -snake_block, 0
                elif event.key == pygame.K_RIGHT:
                    x1_change, y1_change = snake_block, 0
                elif event.key == pygame.K_UP:
                    x1_change, y1_change = 0, -snake_block
                elif event.key == pygame.K_DOWN:
                    x1_change, y1_change = 0, snake_block

        x1, y1 = (x1 + x1_change) % dis_width, (y1 + y1_change) % dis_height

        dis.fill(blue)

        pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])

	    # Ajout de la position de la tete du serpent
        snake_head = (x1, y1)
        snake_list.append(snake_head)
        # Suppression si necessaire de la queue du serpent
        if len(snake_list) > length_of_snake:
            del snake_list[0]

        # Teste si le serpent rencontre son corps
        for position in snake_list[:-1]:
            if position == snake_head:
                game_close = True

        # Dessin du serpent
        our_snake(snake_block, snake_list)

        pygame.display.update()

        # Serpent mange la nourriture
        if x1 == foodx and y1 == foody:
            message("Miam!!", red)
            pygame.display.update()
            length_of_snake += 1
            # Nouvelle nourriture
            foodx = round(random.randrange(0, dis_width - snake_block)/10)*10
            foody = round(random.randrange(0, dis_height - snake_block)/10)*10
            time.sleep(2)

        clock.tick(snake_speed)
							     
    pygame.quit()
    quit()
    
gameLoop()
</pre>

<h2>
Exercices
</h2>
<ol>
  <li>Modifier la couleur de la tête du serpent.</li>
  <li>Modifier la rapidité du serpent.</li>
</ol>


<h1 id="Score">
  Décompte et affichage du score
</h1>

Finalement, nous allons compter le nombre de nourritures ingurgitées par le serpent et afficher ce score dans un coin de l'écran.
<pre id="09-serpent_score">
import pygame
import time
import random

pygame.init()

dis_width, dis_height = 800, 600
snake_block = 10
snake_speed = 15

white = (255, 255, 255)
yellow = (255, 255, 102)
black = (0, 0, 0)
red = (255, 0, 0)
green = (0, 255, 0)
blue = (0, 0, 225)

dis = pygame.display.set_mode((dis_width, dis_height))
pygame.display.set_caption("Jeu du serpent")

clock = pygame.time.Clock()

font_style = pygame.font.SysFont(None, 25)
score_font = pygame.font.SysFont("comicsansms", 35) # Fonte du score

def your_score(score):
    """score : score du joueur
    Affiche le score en haut a gauche de l ecran"""
    value = score_font.render("Votre score : "+str(score), True, yellow)
    dis.blit(value, [0, 0])

def message(msg, color):
    """msg : chaine de caracter
    color : couleur
    Affiche le message msg en couleur color"""
    mesg = font_style.render(msg, True, color)
    text_rect = mesg.get_rect(center=(dis_width/2, dis_height/2))
    dis.blit(mesg, text_rect)

def our_snake(snake_block, snake_list):
    """snake_block : taille du serpent
    snake_list : positions du corps du serpent
    dessine le serpent sur l ecran"""
    for i in range(0, len(snake_list)-1):
        x, y = snake_list[i]
        pygame.draw.rect(dis, black, [x, y, snake_block, snake_block])
    x, y = snake_list[-1]
    pygame.draw.rect(dis, red, [x, y, snake_block, snake_block])

def gameLoop():
    game_over = False
    game_close = False

    x1, y1 = dis_width/2, dis_height/2
    x1_change, y1_change = 0, 0

    snake_list = []
    length_of_snake = 1
    local_snake_speed = snake_speed

    foodx = round(random.randrange(0, dis_width - snake_block)/10)*10
    foody = round(random.randrange(0, dis_height - snake_block)/10)*10

    while not game_over:
        while game_close:
            dis.fill(blue)
            message("Vous avez perdu ! Taper sur 'q' pour quitter et 'n' pour jouer une nouvelle partie", red)	     
            pygame.display.update()
            for event in pygame.event.get():
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_q:
                        game_over = True
                        game_close = False
                    if event.key == pygame.K_n:
                        gameLoop()

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                game_over = True
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    x1_change, y1_change = -snake_block, 0
                elif event.key == pygame.K_RIGHT:
                    x1_change, y1_change = snake_block, 0
                elif event.key == pygame.K_UP:
                    x1_change, y1_change = 0, -snake_block
                elif event.key == pygame.K_DOWN:
                    x1_change, y1_change = 0, snake_block


        x1, y1 = (x1 + x1_change) % dis_width, (y1 + y1_change) % dis_height


        dis.fill(blue)


        pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])

        snake_head = (x1, y1)
        snake_list.append(snake_head)
        if len(snake_list) > length_of_snake:
            del snake_list[0]

        for position in snake_list[:-1]:
            if position == snake_head:
                game_close = True

        our_snake(snake_block, snake_list)
        # Ajout du score
        your_score(length_of_snake - 1)

        pygame.display.update()

        if x1 == foodx and y1 == foody:
            message("Miam!!", red)
            pygame.display.update()
            length_of_snake += 1
            foodx = round(random.randrange(0, dis_width - snake_block)/10)*10
            foody = round(random.randrange(0, dis_height - snake_block)/10)*10
            time.sleep(2)

        clock.tick(local_snake_speed)
							     
    pygame.quit()
    quit()

gameLoop()
</pre>

<h2>
  Exercices
</h2>
<ol>
  <li>Modifier la couleur d'affichage du score.</li>
  <li>Modifier le code pour que le serpent accélère dès qu'une pomme est mangée.</li>
  <li>Ajouter un obstacle au milieu de l'écran qui engendre la perte du serpent.</li>
</ol>

<h1 id="Obstacles">
Ajout d'un obstacle
</h1>

Nous allons maintenant ajouter des obstacles. Un obstacle est un rectangle. Dans l'exemple, nous n'avons pris qu'un seul exemple, mais il est possible d'en définir plusieurs sur un même écran. La méthode <em>collidelist</em> renvoie -1 si le rectangle ne rencontre aucun obstacle et renvoie le numéro de l'obstacle qu'elle renvoie sinon. Nous prenons également garde à choisir une position de départ du serpent et une position pour la nourriture qui soit en dehors des obstacles.

<pre id="10-serpent_obstacle">
import pygame
import time
import random

pygame.init()

dis_width, dis_height = 800, 600
snake_block = 10
snake_speed = 15

white = (255, 255, 255)
yellow = (255, 255, 102)
black = (0, 0, 0)
red = (255, 0, 0)
green = (100, 255, 100)
blue = (0, 0, 225)
grey = (50, 50, 50)
dark_grey = (20, 20, 20)

dis = pygame.display.set_mode((dis_width, dis_height))
pygame.display.set_caption("Jeu du serpent")

clock = pygame.time.Clock()

font_style = pygame.font.SysFont(None, 25)
score_font = pygame.font.SysFont("comicsansms", 35)

def your_score(score):
    """score : score du joueur
    Affiche le score en haut a gauche de l ecran"""
    value = score_font.render("Votre score : "+str(score), True, yellow)
    dis.blit(value, [0, 0])

def message(msg, color):
    """msg : chaine de caracter
    color : couleur
    Affiche le message msg en couleur color"""
    mesg = font_style.render(msg, True, color)
    text_rect = mesg.get_rect(center=(dis_width/2, dis_height/2))
    dis.blit(mesg, text_rect)

def our_snake(snake_block, snake_list):
    """snake_block : taille du serpent
    snake_list : positions du corps du serpent
    dessine le serpent sur l ecran et renvoie la position de la tete"""
    for i in range(0, len(snake_list)-1):
        x, y = snake_list[i]
        pygame.draw.rect(dis, black, [x, y, snake_block, snake_block])
    x, y = snake_list[-1]
    rect_head = pygame.draw.rect(dis, red, [x, y, snake_block, snake_block])
    return rect_head

# Fonction qui renvoie des positions aleatoires
def random_position(dis_width, dis_height, snake_block):
    """dis_width : largeur de l ecran
    dis_height : hauteur de l ecran
    snake_block : taille de la tete du serpent
    Renvoie des coordonnees aleatoires a l interieur de l ecran"""
    x = round(random.randrange(0, dis_width - snake_block)/10)*10
    y = round(random.randrange(0, dis_height - snake_block)/10)*10
    return x, y

def gameLoop():
    game_over = False
    game_close = False

    current_snake_speed = snake_speed

    # Obstacle
    obstacles = [pygame.draw.rect(dis, dark_grey, [dis_width/2, dis_height/2, dis_width/4, dis_width/4])]


    # Choix d une position de depart en dehors des obstacles
    x1, y1 = dis_width/2, dis_height/2
    rect_head = pygame.draw.rect(dis, red,\
                                 [x1, y1, snake_block, snake_block])
    while rect_head.collidelist(obstacles) != -1:
            x1, y1 = random_position(dis_width, dis_height, snake_block)
            rect_head = pygame.draw.rect(dis, red,\
                                 [x1, y1, snake_block, snake_block])

    x1_change, y1_change = 0, 0

    snake_list = []
    length_of_snake = 1

    # Choix d une nourriture en dehors des obstacles
    foodx, foody = random_position(dis_width, dis_height, snake_block)
    rect_food = pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])
    while rect_food.collidelist(obstacles) != -1:
            foodx, foody = random_position(dis_width, dis_height, snake_block)
            rect_food = pygame.draw.rect(dis, green,\
                                 [foodx, foody, snake_block, snake_block])
 

    while not game_over:
        while game_close:
            dis.fill(grey)
            message("Vous avez perdu ! Taper sur 'q' pour quitter et 'n' pour jouer une nouvelle partie", red)	     
            pygame.display.update()
            for event in pygame.event.get():
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_q:
                        game_over = True
                        game_close = False
                    if event.key == pygame.K_n:
                        gameLoop()

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                game_over = True
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    x1_change, y1_change = -snake_block, 0
                elif event.key == pygame.K_RIGHT:
                    x1_change, y1_change = snake_block, 0
                elif event.key == pygame.K_UP:
                    x1_change, y1_change = 0, -snake_block
                elif event.key == pygame.K_DOWN:
                    x1_change, y1_change = 0, snake_block

        dis.fill(grey)
        rect_food = pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])
        # Trace des obstacles
        obstacles = [pygame.draw.rect(dis, dark_grey, [dis_width/2, dis_height/2, dis_width/4, dis_width/4])]
        
        x1, y1 = (x1 + x1_change) % dis_width, (y1 + y1_change) % dis_height

        snake_head = (x1, y1)
        snake_list.append(snake_head)
        if len(snake_list) > length_of_snake:
            del snake_list[0]

        for position in snake_list[:-1]:
            if position == snake_head:
                game_close = True

        # Nouvelle position de la tete
        rect_head = our_snake(snake_block, snake_list)
        your_score(length_of_snake - 1)
                   
        # Si la tete rencontre un obstacle
        if rect_head.collidelist(obstacles) != -1:
            game_close = True
        
        pygame.display.update()

        if x1 == foodx and y1 == foody:
            message("Miam!!", red)
            pygame.display.update()
            length_of_snake += 1

            current_snake_speed += 1
			# Choix d une nourriture en dehors des obstacles
            foodx, foody = random_position(dis_width, dis_height, snake_block)
            rect_food = pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])
            while rect_food.collidelist(obstacles) != -1:
                foodx, foody = random_position(dis_width, dis_height, snake_block)
                rect_food = pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])

            time.sleep(2)

        clock.tick(current_snake_speed)
        
    pygame.quit()
    quit()

gameLoop()
</pre>

<Exercices>
<ol>
<li>Modifier l'obstacle existant.</li>
<li>Ajouter plusieurs obstacles sur le même écran.</li>
</ol>

<h1 id="Niveaux">
Ajout de niveaux
</h1>

Nous allons maintenant ajouter différents niveaux au jeu. Dans le code suivant, les niveaux seront passés tous les 3 points de score. La fonction <em>obstacles</em> permet, étant donné le niveau, de renvoyer une liste d'obstacles. Nous avons également modifié la mise à jour du corps du serpent qui n'est effectuée que lorsque le serpent change de position. Cela permet d'introduire une fonction pause avec la touche <em>K_SPACE</em>
<pre id="11-serpent_niveaux">
import pygame
import time
import random

pygame.init()

dis_width, dis_height = 800, 600
snake_block = 10
snake_speed = 15

white = (255, 255, 255)
yellow = (255, 255, 102)
black = (0, 0, 0)
red = (255, 0, 0)
green = (100, 255, 100)
blue = (0, 0, 225)
grey = (50, 50, 50)
dark_grey = (20, 20, 20)

dis = pygame.display.set_mode((dis_width, dis_height))
pygame.display.set_caption("Jeu du serpent")

clock = pygame.time.Clock()

font_style = pygame.font.SysFont(None, 25)
score_font = pygame.font.SysFont("comicsansms", 35) # Fonte du score

def your_score(score):
    """score : score du joueur
    Affiche le score en haut a gauche de l ecran"""
    value = score_font.render("Votre score : "+str(score), True, yellow)
    dis.blit(value, [0, 0])

def message(msg, color):
    """msg : chaine de caracter
    color : couleur
    Affiche le message msg en couleur color"""
    mesg = font_style.render(msg, True, color)
    text_rect = mesg.get_rect(center=(dis_width/2, dis_height/2))
    dis.blit(mesg, text_rect)

def our_snake(snake_block, snake_list):
    """snake_block : taille du serpent
    snake_list : positions du corps du serpent
    dessine le serpent sur l ecran et renvoie la position de la tete"""
    for i in range(0, len(snake_list)-1):
        x, y = snake_list[i]
        pygame.draw.rect(dis, black, [x, y, snake_block, snake_block])
    x, y = snake_list[-1]
    rect_head = pygame.draw.rect(dis, red, [x, y, snake_block, snake_block])
    return rect_head

def random_position(dis_width, dis_height, snake_block):
    """dis_width : largeur de l ecran
    dis_height : hauteur de l ecran
    snake_block : taille de la tete du serpent
    Renvoie des coordonnees aleatoires a l interieur de l ecran"""
    x = round(random.randrange(0, dis_width - snake_block)/10)*10
    y = round(random.randrange(0, dis_height - snake_block)/10)*10
    return x, y

def obstacles(level):
    """level : entier designant le niveau du jeu
    renvoie la liste d obstacles associee au niveau"""
    if level == 0:
        return []
    elif level == 1:
        return [
            pygame.draw.rect(dis, dark_grey, [dis_width/2, dis_height/2, dis_width/4, dis_width/4])]
    elif level == 2:
        return [
            pygame.draw.rect(dis, dark_grey, [0, dis_height/2, dis_width, dis_width/4])]
    else:
            return [\
                    pygame.draw.rect(dis, dark_grey, [dis_width/2, dis_height/2, dis_width/4, dis_width/4]),\
                    pygame.draw.rect(dis, dark_grey, [dis_width/4, dis_height/4, dis_width/4, dis_width/4]),]

def gameLoop():
    game_over = False
    game_close = False

    level = 0
    score = 0
    length_of_snake = 1
    current_snake_speed = snake_speed
    
    # Obstacles
    rect_obs = obstacles(level)
    
    # Choix d une position de depart en dehors des obstacles
    x1, y1 = dis_width/2, dis_height/2
    rect_head = pygame.draw.rect(dis, red,\
                                 [x1, y1, snake_block, snake_block])
    while rect_head.collidelist(rect_obs) != -1:
            x1, y1 = random_position(dis_width, dis_height, snake_block)
            rect_head = pygame.draw.rect(dis, red,\
                                 [x1, y1, snake_block, snake_block])

    x1_change, y1_change = 0, 0
    snake_list = [(x1, y1)]

    # Choix d une nourriture en dehors des obstacles
    foodx, foody = random_position(dis_width, dis_height, snake_block)
    rect_food = pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])
    while rect_food.collidelist(rect_obs) != -1:
            foodx, foody = random_position(dis_width, dis_height, snake_block)
            rect_food = pygame.draw.rect(dis, green,\
                                 [foodx, foody, snake_block, snake_block])

    while not game_over:
        while game_close:
            dis.fill(grey)
            message("Vous avez perdu ! Taper sur 'q' pour quitter et 'n' pour jouer une nouvelle partie", red)	     
            pygame.display.update()
            for event in pygame.event.get():
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_q:
                        game_over = True
                        game_close = False
                    if event.key == pygame.K_n:
                        gameLoop()

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                game_over = True
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    x1_change, y1_change = -snake_block, 0
                elif event.key == pygame.K_RIGHT:
                    x1_change, y1_change = snake_block, 0
                elif event.key == pygame.K_UP:
                    x1_change, y1_change = 0, -snake_block
                elif event.key == pygame.K_DOWN:
                    x1_change, y1_change = 0, snake_block
                elif event.key == pygame.K_SPACE:
                    x1_change, y1_change = 0, 0



        dis.fill(grey)
        rect_food = pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])

        x1, y1 = (x1 + x1_change) % dis_width, (y1 + y1_change) % dis_height

        # Trace des obstacles
        rect_obs = obstacles(level)

        if (x1_change, y1_change) != (0, 0):
            snake_head = (x1, y1)
            snake_list.append(snake_head)
            if len(snake_list) > length_of_snake:
                del snake_list[0]

            for position in snake_list[:-1]:
                if position == snake_head:
                    game_close = True

        rect_head = our_snake(snake_block, snake_list)
        # Ajout du score
        your_score(score)
                   
        rect_obs = obstacles(level)
        
        if rect_head.collidelist(rect_obs) != -1:
            game_close = True
        
        pygame.display.update()

        if x1 == foodx and y1 == foody:
            message("Miam!!", red)
            pygame.display.update()
            length_of_snake += 1
            score += 1
            if score % 3 == 0:
                level += 1
                rect_obs = obstacles(level)

            current_snake_speed += 1
            # Nouvelle position de depart (eventuellement)
            rect_head = pygame.draw.rect(dis, red,\
                                 [x1, y1, snake_block, snake_block])
            while rect_head.collidelist(rect_obs) != -1:
                x1, y1 = random_position(dis_width, dis_height, snake_block)
                rect_head = pygame.draw.rect(dis, red,\
                                 [x1, y1, snake_block, snake_block])

            # Nouvelle nourriture            
            foodx, foody = random_position(dis_width, dis_height, snake_block)
            rect_food = pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])
            while rect_food.collidelist(rect_obs) != -1:
                foodx, foody = random_position(dis_width, dis_height, snake_block)
                rect_food = pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])

            time.sleep(2)

        clock.tick(current_snake_speed)
        
    pygame.quit()
    quit()

gameLoop()
</pre>

<h2>
Exercices
</h2>
<ol>
<li>Modifier le score nécessaire pour changer de niveau.</li>
<li>Afficher le niveau sur l'écran.</li>
<li>Modifier et ajouter des niveaux.</li>
</ol>

<h1 id="Statistiques">
  Enregistrement des statistiques
</h1>

Les statistiques des joueurs vont être stockées dans un fichier <em>JSON</em>. La commande <em>open</em> permet d'ouvrir le fichier, puis de lire son contenu via la commande <em>load</em> du module <em>json</em> et enfin de le stocker dans un dictionnaire. L'alternative <em>try</em> permet de créer un dictionnaire vide si le fichier de statistiques n'existe pas.

Au démarrage du jeu, la fonction <em>ask_for_user()</em> affiche une invitation à saisir son nom. Le nom est validé en appuant sur la touche <em>K_RETURN</em>.

À la fin de la partie, les données sont ensuite enregistrées en précisant la date et l'heure de la fin du jeu.

Les statistiques peuvent ensuite être affichées en cliquant sur <em>K_s</em>

<pre id="12-serpent_statistiques">
import pygame
import time
import random
import json # Permet de stocker les donnees au format json

pygame.init() # Initialise l environnement

# Chargement des statistiques
try:
    with open("snake_score.json", "r") as score_file:
        # Charger le fichier s il existe sous forme de dictionnaire
        data = json.load(score_file)
except:
    # Creation du dictionnaire vide si le fichier n existe pas
    data = {}

dis_width, dis_height = 800, 600 # Dimensions de l ecran
snake_block = 10 # Taille du serpent
snake_speed = 15 # Rapidite du serpent

white = (255, 255, 255)
yellow = (255, 255, 102)
black = (0, 0, 0)
red = (255, 0, 0)
green = (0, 255, 0)
blue = (0, 0, 225)
grey = (50, 50, 50)
dark_grey = (20, 20, 20)

dis = pygame.display.set_mode((dis_width, dis_height))
pygame.display.set_caption("Jeu du serpent")

clock = pygame.time.Clock()

msg_font_size = 25
font_style = pygame.font.SysFont(None, msg_font_size)
score_font_size = 35
score_font = pygame.font.SysFont("comicsansms", score_font_size)


def statistics(dis):
    run = True
    while run:
        for event in pygame.event.get():
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_q:
                    # Enregistrement des statistiques
                    run = False
                    game_over = True
                    game_close = False
                elif event.key == pygame.K_n:
                    run = False
                    gameLoop()
        dis.fill(grey)
        with open("snake_score.json", "r") as score_file:
            # Charger le fichier s il existe sous forme de dictionnaire
            data = json.load(score_file)
        number_cols = len(data)
        counter = 0
        for nom in data:
            x = counter * dis_width//number_cols
            scores = sorted(data[nom], reverse=True)
            v = score_font.render(nom, True, yellow)
            dis.blit(v, [x, 0])
            for (line, s) in enumerate(scores):
                v = score_font.render(str(s[0]) + ", " + s[1].split(" ")[0], True, yellow)
                dis.blit(v, [x, (line + 1) * msg_font_size])
            counter += 1
        pygame.display.flip()

            
def ask_for_user():
    text = ""
    input_active = True
    font = pygame.font.SysFont(None, 35)
    run = True
    while run:
        clock.tick(60)
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                run = False
            elif event.type == pygame.MOUSEBUTTONDOWN:
                input_active = True
                text = ""
            elif event.type == pygame.KEYDOWN and input_active:
                if event.key == pygame.K_RETURN:
                    input_active = False
                    return text
                elif event.key == pygame.K_BACKSPACE:
                    text =  text[:-1]
                else:
                    text += event.unicode
            
            dis.fill(0)
            text_surf = font.render("Utilisateur = "+text, True, (255, 0, 0))
            dis.blit(text_surf, text_surf.get_rect(center = dis.get_rect().center))
            pygame.display.flip()
            

def your_score(level, score):
    """level : niveau du jeu
    score : score du joueur
    Affiche le niveau et le score en haut a gauche de l ecran"""
    value = [score_font.render("Votre niveau : "+str(level), True, yellow),
             score_font.render("Votre score : "+str(score), True, yellow)
             ]
    for line in range(len(value)):
        dis.blit(value[line], (0,line*score_font_size))

def message(msg, color):
    """msg : chaine de caracter
    color : couleur
    Affiche le message msg en couleur color"""
    mesg = []
    for m in msg:
        mesg.append(font_style.render(m, True, color))
    text_rect = []
    for line in range(len(mesg)):
        text_rect.append(mesg[line].get_rect(center=(dis_width/2, dis_height/2 + line * msg_font_size)))
    for line in range(len(text_rect)):
        dis.blit(mesg[line], text_rect[line])


        # dis.blit(text_rect[line], (0,line*score_font_size))
    
    # text_rect = 

def our_snake(snake_block, snake_list):
    """snake_block : taille du serpent
    snake_list : positions du corps du serpent
    dessine le serpent sur l ecran et renvoie la position de la tete"""
    for i in range(0, len(snake_list)-1):
        x, y = snake_list[i]
        pygame.draw.rect(dis, black, [x, y, snake_block, snake_block])
    x, y = snake_list[-1]
    rect_head = pygame.draw.rect(dis, red, [x, y, snake_block, snake_block])
    return rect_head

def random_position(dis_width, dis_height, snake_block):
    """dis_width : largeur de l ecran
    dis_height : hauteur de l ecran
    snake_block : taille de la tete du serpent
    Renvoie des coordonnees aleatoires a l interieur de l ecran"""
    x = round(random.randrange(0, dis_width - snake_block)/10)*10
    y = round(random.randrange(0, dis_height - snake_block)/10)*10
    return x, y

def obstacles(level):
    """level : entier designant le niveau du jeu
    renvoie la liste d obstacles associee au niveau"""
    if level == 0:
        return []
    elif level == 1:
        return [
            pygame.draw.rect(dis, dark_grey, [dis_width/2, dis_height/2, dis_width/4, dis_width/4])]
    elif level == 2:
        return [
            pygame.draw.rect(dis, dark_grey, [0, dis_height/2, dis_width, dis_width/4])]
    else:
            return [\
                    pygame.draw.rect(dis, dark_grey, [dis_width/2, dis_height/2, dis_width/4, dis_width/4]),\
                    pygame.draw.rect(dis, dark_grey, [dis_width/4, dis_height/4, dis_width/4, dis_width/4]),]

        
def gameLoop():
    # Demande de l utilisateur et creation de sa liste de scores
    user = ask_for_user()
    if user not in data:
        data[user] = []

    game_over = False
    game_close = False

    level = 0
    score = 0
    length_of_snake = 1
    current_snake_speed = snake_speed

    rect_obs = obstacles(level)
    
    x1, y1 = dis_width/2, dis_height/2
    rect_head = pygame.draw.rect(dis, red,\
                                 [x1, y1, snake_block, snake_block])
    while rect_head.collidelist(rect_obs) != -1:
            x1, y1 = random_position(dis_width, dis_height, snake_block)
            rect_head = pygame.draw.rect(dis, red,\
                                 [x1, y1, snake_block, snake_block])

    x1_change, y1_change = 0, 0
    snake_list = [(x1, y1)]

    foodx, foody = random_position(dis_width, dis_height, snake_block)
    rect_food = pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])
    while rect_food.collidelist(rect_obs) != -1:
            foodx, foody = random_position(dis_width, dis_height, snake_block)
            rect_food = pygame.draw.rect(dis, green,\
                                 [foodx, foody, snake_block, snake_block])

    while not game_over:
        while game_close:
            dis.fill(grey)
            message(["Vous avez perdu !",\
                     "`q` : quitter",\
                     "`n` : nouvelle partie",\
                     "`s` : statistiques"], red)	     
            pygame.display.update()
            # Enregistrement des statistiques
            t = time.localtime()
            current_time = time.strftime("%Y-%-m-%-d %H:%M:%S", t)

            for event in pygame.event.get():
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_q:
                        # Enregistrement des statistiques
                        data[user].append((score, current_time))
                        with open("snake_score.json", "w") as score_file:
                            json.dump(data, score_file)
                        game_over = True
                        game_close = False
                    elif event.key == pygame.K_n:
                         # Enregistrement des statistiques
                        data[user].append((score, current_time))
                        with open("snake_score.json", "w") as score_file:
                            json.dump(data, score_file)
                        gameLoop()
                    elif event.key == pygame.K_s:
                        # Enregistrement des statistiques
                        data[user].append((score, current_time))
                        with open("snake_score.json", "w") as score_file:
                            json.dump(data, score_file)
                        statistics(dis)
                        
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                game_over = True
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    x1_change, y1_change = -snake_block, 0
                elif event.key == pygame.K_RIGHT:
                    x1_change, y1_change = snake_block, 0
                elif event.key == pygame.K_UP:
                    x1_change, y1_change = 0, -snake_block
                elif event.key == pygame.K_DOWN:
                    x1_change, y1_change = 0, snake_block
                elif event.key == pygame.K_SPACE:
                    x1_change, y1_change = 0, 0

        dis.fill(grey)
        rect_food = pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])

        x1, y1 = (x1 + x1_change) % dis_width, (y1 + y1_change) % dis_height

        rect_obs = obstacles(level)

        if (x1_change, y1_change) != (0, 0):
            snake_head = (x1, y1)
            snake_list.append(snake_head)
            if len(snake_list) > length_of_snake:
                del snake_list[0]

            for position in snake_list[:-1]:
                if position == snake_head:
                    game_close = True

        rect_head = our_snake(snake_block, snake_list)

        your_score(level, score)
                   
        rect_obs = obstacles(level)
        
        if rect_head.collidelist(rect_obs) != -1:
            game_close = True
        
        pygame.display.update()

        if x1 == foodx and y1 == foody:
            message(["Miam!!"], red)
            pygame.display.update()
            length_of_snake += 1
            score += 1
            if score % 3 == 0:
                level += 1
                rect_obs = obstacles(level)

            current_snake_speed += 1

            rect_head = pygame.draw.rect(dis, red,\
                                 [x1, y1, snake_block, snake_block])
            while rect_head.collidelist(rect_obs) != -1:
                x1, y1 = random_position(dis_width, dis_height, snake_block)
                rect_head = pygame.draw.rect(dis, red,\
                                 [x1, y1, snake_block, snake_block])


            foodx, foody = random_position(dis_width, dis_height, snake_block)
            rect_food = pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])
            while rect_food.collidelist(rect_obs) != -1:
                foodx, foody = random_position(dis_width, dis_height, snake_block)
                rect_food = pygame.draw.rect(dis, green, [foodx, foody, snake_block, snake_block])

            time.sleep(2)

        clock.tick(current_snake_speed)
							     
    pygame.quit()
    quit()

gameLoop()
</pre>
