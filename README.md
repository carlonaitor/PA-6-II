with open('tvShows.txt') as tvShows:
        txt = tvShows.readlines()

dict_shows = {}

for s in txt:
        x = s.split(',')
        dict_shows[x[0]] = [int(x[1]),float(x[2])]

with open('output_showNames.txt', 'w') as output:
        for s in sorted(dict_shows):
                output.write(s)
                output.write('\n')


seasons = []
ratings = []

for v in dict_shows.values():
        seasons.append(v[0])
        ratings.append(v[1])


seasons = sorted(seasons, reverse = True)
names_by_seasons = []
for s in seasons:
        for k, v in dict_shows.items():
                if s == v[0]:
                        if not k in names_by_seasons:
                                names_by_seasons.append(k)

with open('output_showSeasons.txt', 'w') as output:
        for s in str(seasons):
                output.write(s)
                
with open('output_showsBySeasons.txt', 'w') as output:
        for s in names_by_seasons:
                output.write(s)
                output.write('\n')


ratings = sorted(ratings)
names_by_ratings = []
for r in ratings:
        for k, v in dict_shows.items():
                if r == v[1]:
                        if not k in names_by_ratings:
                                names_by_ratings.append(k)

with open('output_showRatings.txt', 'w') as output:
        for s in str(ratings):
                output.write(s)

with open('output_showsByRatings.txt', 'w') as output:
        for s in names_by_ratings:
                output.write(s)
                output.write('\n')

##################################################################################
'''
Created on Fri Nov 13 09:38:24 2020
@author: aisli
'''

import matplotlib.pyplot as plt

shadesofblue = ['xkcd:aqua','xkcd:azure','xkcd:cyan','xkcd:lightblue','xkcd:bluey grey']
allorange = ['xkcd:orange','xkcd:rusty orange','xkcd:yellowish orange','xkcd:mango','xkcd:pumpkin orange']
allpink = ['xkcd:bubblegum pink','xkcd:barbie pink','xkcd:neon pink','xkcd:fuchsia','xkcd:deep pink']
neon = ['xkcd:lime yellow','xkcd:purple/pink','xkcd:toxic green','xkcd:hot magenta','xkcd:vermillion']
pastels = ['xkcd:blush','xkcd:lavender pink','xkcd:pale green','xkcd:baby blue','xkcd:banana',]
yuck = ['xkcd:puke','xkcd:mustard yellow','xkcd:mud','xkcd:dirty orange','xkcd:pea soup',]
grays = ['xkcd:silver','xkcd:steel grey','xkcd:cool grey','xkcd:battleship grey','xkcd:grey']

title1 = 'Top 5 Ratings Plot'
ys_plt1 = []
xs_plt1 = []
color1 = yuck

title2 = 'Top 5 Seasons Plot'
ys_plt2 = []
xs_plt2 = []
color2 = neon
#######################################################################################
'''
Created on Fri Nov 13 09:38:24 2020
@author: aisli
'''

fig1 = plt.figure(figsize=(8,5))
plt1 = plt.bar(range(len(xs_plt1)),height=ys_plt1,color=color1)
plt.title(title1)
plt.xticks(range(len(xs_plt1)),xs_plt1,rotation='vertical')
plt.margins(0.2)
plt.show()
fig1.savefig(title1+'.png', dpi=fig1.dpi)

fig2 = plt.figure(figsize=(8,5))
plt2 = plt.bar(range(len(xs_plt2)),height=ys_plt2,color=color2)
plt.title(title2)
plt.xticks(range(len(xs_plt2)),xs_plt2,rotation='vertical')
plt.margins(0.2)
plt.show()
fig2.savefig(title2+'.png', dpi=fig2.dpi)
########################################################################################
xs_plt2.append(names_by_seasons[0:5])
ys_plt2.append(seasons[0:5])


xs_plt1.append(names_by_ratings[0:5])
ys_plt1.append(sorted(ratings[0:5], reverse = True))

