# Interpolacao
#Interpolação de lagrange como funçãomatematica
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

dados = [
    ["EI", 784, 1131, 1445, 1782, 2143],
    ["EB", 838, 1240, 1634, 2069, 2386],
    ["ES", 1233, 1807, 2487, 3111, 3698],
    ["EG", 1672, 2330, 3290, 4145, 5666]
    ]
df = pd.DataFrame(data=dados,columns=[' ','1975','1980','1985','1990','1995'])
print('---------- INTERPOLAÇÃO DE LAGRANGE -------------')
print( df.head())

def interpLagrange(xp,x,y,grau):
  yp = 0
  for k in range(0,n+1):
    p = 1
    for j in range(0,n+1):
      if k != j:
        p = p*(xp - x[j])/(x[k] - x[j])

    yp = yp + p * y[k]

  return yp

#dados da matriz separados por niveis de escolaridade

x =  [1975,1980,1985,1990,1995]
EI = [784, 1131, 1445, 1782, 2143]
EB = [838, 1240, 1634, 2069, 2386]
ES = [1233, 1807, 2487, 3111, 3698]
EG = [ 1672, 2330, 3290, 4145, 5666]

nivel =str(input('Qual é a sigla de escolaridade (EI,EB,ES,EP): '))
if nivel =='EI': 
     y= EI
elif nivel =='EB': 
     y= EB
elif nivel =='ES': 
     y= ES
elif nivel =='EG':
     y=EG
else:
     print('Você tem que digitar a sigla correspondente (EI,EB,ES,EP): ')

xp = int(input('Digite o ano em que deseja descobrir a média: '))
n = 4
yp = interpLagrange(xp,x,y,n)
t  = np.arange(1970,2000,5)
yt = []
print('O resultado é',yp)
for i in t:
  yt.append(interpLagrange(i,x,y,n))
plt.plot(t,yt,'b-')
plt.plot(x,y,'ro')
plt.plot(xp,yp,'g*')

plt.show()


