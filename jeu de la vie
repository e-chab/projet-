from random import randint
import ssd1306

def jeudelavie(a,b):
    # Init Voisins
    Voisins=[[0 for col in range(b)] for lig in range(a)]
    # Init Nouv
    Nouv=[[0 for col in range(b)] for lig in range(a)]

    # Random_Grid
    Liste=[[0 for col in range(b)] for lig in range(a)] # Fill Liste with Zeros
    for lig in range(a):
      for col in range(b):
        Liste[lig][col]=randint(0,1) # Random initialisation with 0 & 1 (Too Long : randint(1,100)%2)
        if Liste[lig][col] == 1:
          # Display / Graphics
          # Pixel X position
          # Pixel Y position
          # Pixel color (0 = black, 1 = white)
          afficheur.pixel(lig, col, 1) # Display one Dot
          afficheur.show()      

    # Life
    for gen in range(1000): # For 1000 Générations !
      print(gen)
      for i in range(a):
        for j in range(b):
          Voisins[i][j]=0
          for k in [-1,0,1]:
            for l in [-1,0,1]:        
              if (k,l)!=(0,0) and (0<=(i+k)<=(a-1) and 0<=(j+l)<=(b-1)):
                Voisins[i][j]+=Liste[(i+k)][(j+l)]

      for m in range(a):
        for n in range(b):
          if ( Liste[m][n]==0 and Voisins[m][n]==3 ) or ( Liste[m][n]==1 and Voisins[m][n] in [2,3] ): # Live or Death ?
            # Life
            Nouv[m][n]=1
            couleur=1
          else:
            # Death
            Nouv[m][n]=0
            couleur=0
          if Nouv[m][n]!=Liste[m][n]:
            afficheur.pixel(m, n, couleur) # Display Nouv Grid
            afficheur.show()
          Liste[m][n]=Nouv[m][n]


# afficheur branché en i2c (clock sur la pin B8 et data sur la pin B9)
connexion_i2c = machine.SoftI2C(scl=machine.Pin('B8'), sda=machine.Pin('B9'))
# initialisation afficheur (de 128 pixels par 64)
afficheur = ssd1306.SSD1306_I2C(128,64,connexion_i2c)
# remise à 0
afficheur.fill(0)
afficheur.show()

jeudelavie(128,64)
