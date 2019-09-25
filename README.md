# What2Play
# I love Dota 2 and want to test my skills of Python
# So here we go. A small tool that tells which heroes to play
import random
class Hero:
#lists of heroes of every role
    carry = ['Antimage', 'Alchemist', 'Luna', 'Wraith King', 'Juggernaut', 'Phantom Assassin', 'Phantom Lancer', 'Morphling', 'Medusa', 'Drow Ranger', 'Naga Siren']
    mid =['Lina', 'Shadow Fiend', 'Storm Spirit', 'Tinker', 'Windranger', 'Pugna', 'Puck', 'Invoker', 'Tiny','Dragon Knight', 'Zeus']
    offlane = ['Nature\'s Prophet', 'Tidehunter', 'Centaur', 'Batrider', 'Legion Commander', 'Timbersaw','Axe', 'Bristleback', 'Clockwerk' ]
    soft_support = ['Lion', 'Shadow Shaman', 'Wisp', 'Earthshaker', 'Visage', 'Enchantress', 'Nyx Assassin', 'Tusk', 'Rubick', 'Mirana']
    full_support = ['Lich', 'Kaldr', 'Bane', 'Jakiro', 'Warlock', 'Oracle', 'Crystal Maiden', 'Disruptor', 'Silencer', 'Abbadon', 'Ezalor']
    def __init__(self, name):
        self.name = name
    def check(self):     #A method to check what kind of hero the user input
        self.counter = 0   # A variable that collects in-game position(role) of the input heroes
        if self.name in Hero.carry :
            Hero.carry.remove(self.name)
            self.counter = 1
            return self.counter
        elif self.name in Hero.mid:
            Hero.mid.remove(self.name)
            self.counter = 2
            return self.counter 
        elif self.name in Hero.offlane:
            Hero.offlane.remove(self.name)
            self.counter =3
            return self.counter
        elif self.name in Hero.soft_support:
            Hero.soft_support.remove(self.name)
            self.counter =4
            return self.counter
        elif self.name in Hero.full_support:
            Hero.full_support.remove(self.name)
            self.counter =5
            return self.counter
        else:
            raise NameError(f'There\'s no such hero as {self.name}')
    def tip (counter):  # A method to recommend heroes, based on 'counter'
        rec_list = []
        if counter < 7:
            for i in range(0,4):
                j = random.randint(0, len(Hero.carry)-1)
                rec_list.append(Hero.carry[j])
                Hero.carry.remove(Hero.carry[j])                
            print('You are a carry player. Try out these heroes: ' +', '.join(rec_list))
        elif  7 <= counter<13:
            for i in range(1,5):
                j= random.randint(0, len(Hero.mid)-1)
                rec_list.append(Hero.mid[j])
                Hero.mid.remove(Hero.mid[j])   
            print('You are a mid player. Try out these heroes: ' +', '.join(rec_list))
        elif 13 <= counter < 18:
            for i in range(1,5):
                j = random.randint(0, len(Hero.offlane)-1)
                rec_list.append(Hero.offlane[j])
                Hero.offlane.remove(Hero.offlane[j])
            print('You are an offlane player. Try out these heroes: ' + ', '.join(rec_list))
        elif 18 <= counter < 22:
            for i in range(1,5):
                j = random.randint(0, len(Hero.soft_support) -1)
                rec_list.append(Hero.soft_support[j])
                Hero.soft_support.remove(Hero.soft_support[j])
            print ('You are a fourth position player. Try out these heroes: ' + ', '.join(rec_list))
        else:
            for i in range(1,5):
                j = random.randint(0,len(Hero.full_support)-1)
                rec_list.append(Hero.full_support[j])
                Hero.full_support.remove(Hero.support[j])
            print('You are a full-support player. Try out these heroes: ' + ', '.join(rec_list))
a = input('Enter your most favourite hero: ')
b = input('Enter your second favourite hero: ')
c = input('Enter your third favourite hero: ')
d = input('Enter your fourth favourite hero: ')
e = input('Enter your fifth favourite hero: ')
A = Hero(a)
B = Hero(b)
C = Hero(c)
D = Hero(d)
E = Hero(e)
res = A.check()+ B.check() +C.check()+ D.check()+ E.check()
Hero.tip(res)
