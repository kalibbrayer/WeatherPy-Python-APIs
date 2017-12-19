

```python
# Dependencies
import matplotlib.pyplot as plt
import requests as req
import pandas as pd
import random
```


```python
# Save config information.
api_key = "8fbe995b2605abe6003ad5b588d1c19a"
url = 'http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=' 
key = '&APPID=' + api_key
```


```python
city_df = pd.read_json("city.list.json")
```


```python
city_df.columns
```




    Index(['coord', 'country', 'id', 'name'], dtype='object')




```python
city_df = city_df[["name", "id"]].sample(n=500)
```


```python
cities = city_df["name"].values 
city_id = city_df.id.values
```


```python
weather_data = []
lat_data = []
temp_data = [ ]
humidity_data = []
cloudiness_data = []
windspeed_data = []
lon_data = []
country_data = [] 
date_data = []

# Loop through the list of cities and perform a request for data on each 
i = 0 
for city in city_id:
    response = req.get(url + str(city) + key).json() 
    if response.get("coord").get("lat") is None: 
        print(city)
    date_data.append(response.get("dt")) 
    country_data.append(response.get("sys").get("country"))
    lat_data.append(response.get("coord").get("lat"))
    lon_data.append(response.get("coord").get("lon"))
    temp_data.append(response.get("main").get("temp_max"))
    humidity_data.append(response.get("main").get("humidity"))
    cloudiness_data.append(response.get("clouds").get("all")) 
    windspeed_data.append(response.get("wind").get("speed"))
    print(str(i+1)+" City ID: "+str(city_id[i])+" City: "+cities[i]+"\n"+url + str(city) + key) 
    i+=1
```

    1 City ID: 2964751 City: County Donegal
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2964751&APPID=8fbe995b2605abe6003ad5b588d1c19a
    2 City ID: 6356260 City: Sant Quirze Safaja
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6356260&APPID=8fbe995b2605abe6003ad5b588d1c19a
    3 City ID: 3121910 City: Fuentelcesped
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3121910&APPID=8fbe995b2605abe6003ad5b588d1c19a
    4 City ID: 2523498 City: San Ferdinando
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2523498&APPID=8fbe995b2605abe6003ad5b588d1c19a
    5 City ID: 3179407 City: Castiglione Olona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3179407&APPID=8fbe995b2605abe6003ad5b588d1c19a
    6 City ID: 7084278 City: Olehsari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7084278&APPID=8fbe995b2605abe6003ad5b588d1c19a
    7 City ID: 3834843 City: Taco Pozo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3834843&APPID=8fbe995b2605abe6003ad5b588d1c19a
    8 City ID: 2989367 City: Orglandes
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2989367&APPID=8fbe995b2605abe6003ad5b588d1c19a
    9 City ID: 2264397 City: Portuguese Republic
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2264397&APPID=8fbe995b2605abe6003ad5b588d1c19a
    10 City ID: 3533426 City: Acayucan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3533426&APPID=8fbe995b2605abe6003ad5b588d1c19a
    11 City ID: 2889720 City: Klein-Bieberau
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2889720&APPID=8fbe995b2605abe6003ad5b588d1c19a
    12 City ID: 3437920 City: Itaquyry
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3437920&APPID=8fbe995b2605abe6003ad5b588d1c19a
    13 City ID: 3117746 City: Madiedo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3117746&APPID=8fbe995b2605abe6003ad5b588d1c19a
    14 City ID: 7873477 City: Sulztal an der Weinstraße
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7873477&APPID=8fbe995b2605abe6003ad5b588d1c19a
    15 City ID: 161974 City: Gazanjyk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=161974&APPID=8fbe995b2605abe6003ad5b588d1c19a
    16 City ID: 652616 City: Kitee
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=652616&APPID=8fbe995b2605abe6003ad5b588d1c19a
    17 City ID: 2613968 City: Sjørring
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2613968&APPID=8fbe995b2605abe6003ad5b588d1c19a
    18 City ID: 6556026 City: Schwendi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6556026&APPID=8fbe995b2605abe6003ad5b588d1c19a
    19 City ID: 6452135 City: Allauch
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6452135&APPID=8fbe995b2605abe6003ad5b588d1c19a
    20 City ID: 6556804 City: Konradsreuth
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6556804&APPID=8fbe995b2605abe6003ad5b588d1c19a
    21 City ID: 1156396 City: Ban Mai
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1156396&APPID=8fbe995b2605abe6003ad5b588d1c19a
    22 City ID: 678358 City: Feldru
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=678358&APPID=8fbe995b2605abe6003ad5b588d1c19a
    23 City ID: 2817114 City: Vitzenburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2817114&APPID=8fbe995b2605abe6003ad5b588d1c19a
    24 City ID: 577429 City: Beregovaya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=577429&APPID=8fbe995b2605abe6003ad5b588d1c19a
    25 City ID: 8013388 City: Mazarefes
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=8013388&APPID=8fbe995b2605abe6003ad5b588d1c19a
    26 City ID: 2613729 City: Skive Kommune
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2613729&APPID=8fbe995b2605abe6003ad5b588d1c19a
    27 City ID: 3837008 City: San Marcos Sierra
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3837008&APPID=8fbe995b2605abe6003ad5b588d1c19a
    28 City ID: 246314 City: Umm as Summaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=246314&APPID=8fbe995b2605abe6003ad5b588d1c19a
    29 City ID: 1855357 City: Nishi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1855357&APPID=8fbe995b2605abe6003ad5b588d1c19a
    30 City ID: 699777 City: Nova Vodolaha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=699777&APPID=8fbe995b2605abe6003ad5b588d1c19a
    31 City ID: 2176739 City: Barrengarry
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2176739&APPID=8fbe995b2605abe6003ad5b588d1c19a
    32 City ID: 570508 City: Buy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=570508&APPID=8fbe995b2605abe6003ad5b588d1c19a
    33 City ID: 787893 City: Mladenovac
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=787893&APPID=8fbe995b2605abe6003ad5b588d1c19a
    34 City ID: 2506385 City: Arzew
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2506385&APPID=8fbe995b2605abe6003ad5b588d1c19a
    35 City ID: 7532585 City: Nowy Sącz
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7532585&APPID=8fbe995b2605abe6003ad5b588d1c19a
    36 City ID: 3001412 City: Les Clairs
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3001412&APPID=8fbe995b2605abe6003ad5b588d1c19a
    37 City ID: 1262669 City: Muddebihal
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1262669&APPID=8fbe995b2605abe6003ad5b588d1c19a
    38 City ID: 2878943 City: Lemgo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2878943&APPID=8fbe995b2605abe6003ad5b588d1c19a
    39 City ID: 7326325 City: Xinghua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7326325&APPID=8fbe995b2605abe6003ad5b588d1c19a
    40 City ID: 3398688 City: Gravatá
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3398688&APPID=8fbe995b2605abe6003ad5b588d1c19a
    41 City ID: 2639964 City: Potton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2639964&APPID=8fbe995b2605abe6003ad5b588d1c19a
    42 City ID: 7065111 City: Sishiba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7065111&APPID=8fbe995b2605abe6003ad5b588d1c19a
    43 City ID: 2839560 City: Scheuern
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2839560&APPID=8fbe995b2605abe6003ad5b588d1c19a
    44 City ID: 3109402 City: Cerdanyola del Valles
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3109402&APPID=8fbe995b2605abe6003ad5b588d1c19a
    45 City ID: 6065395 City: Manor
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6065395&APPID=8fbe995b2605abe6003ad5b588d1c19a
    46 City ID: 6422389 City: Daojiang
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6422389&APPID=8fbe995b2605abe6003ad5b588d1c19a
    47 City ID: 2087362 City: Salamo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2087362&APPID=8fbe995b2605abe6003ad5b588d1c19a
    48 City ID: 2147542 City: Talmalmo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2147542&APPID=8fbe995b2605abe6003ad5b588d1c19a
    49 City ID: 6355931 City: Higuera de Vargas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6355931&APPID=8fbe995b2605abe6003ad5b588d1c19a
    50 City ID: 2148037 City: Stuart Mill
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2148037&APPID=8fbe995b2605abe6003ad5b588d1c19a
    51 City ID: 5152017 City: Deshler
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5152017&APPID=8fbe995b2605abe6003ad5b588d1c19a
    52 City ID: 6355632 City: Ávila
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6355632&APPID=8fbe995b2605abe6003ad5b588d1c19a
    53 City ID: 3618924 City: Jiquilillo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3618924&APPID=8fbe995b2605abe6003ad5b588d1c19a
    54 City ID: 6552374 City: Süpplingenburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6552374&APPID=8fbe995b2605abe6003ad5b588d1c19a
    55 City ID: 4566137 City: Manati
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4566137&APPID=8fbe995b2605abe6003ad5b588d1c19a
    56 City ID: 7413402 City: Sanlanbahai
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7413402&APPID=8fbe995b2605abe6003ad5b588d1c19a
    57 City ID: 5874205 City: Silvertip
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5874205&APPID=8fbe995b2605abe6003ad5b588d1c19a
    58 City ID: 6065536 City: Manvers
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6065536&APPID=8fbe995b2605abe6003ad5b588d1c19a
    59 City ID: 1683852 City: Talisayan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1683852&APPID=8fbe995b2605abe6003ad5b588d1c19a
    60 City ID: 6359822 City: Avión
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6359822&APPID=8fbe995b2605abe6003ad5b588d1c19a
    61 City ID: 3460831 City: Itajuipe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3460831&APPID=8fbe995b2605abe6003ad5b588d1c19a
    62 City ID: 472777 City: Volga
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=472777&APPID=8fbe995b2605abe6003ad5b588d1c19a
    63 City ID: 4319972 City: Church Point
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4319972&APPID=8fbe995b2605abe6003ad5b588d1c19a
    64 City ID: 3130493 City: Aldeanueva de la Sierra
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3130493&APPID=8fbe995b2605abe6003ad5b588d1c19a
    65 City ID: 1957226 City: Ban Louangnamtha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1957226&APPID=8fbe995b2605abe6003ad5b588d1c19a
    66 City ID: 2525749 City: Alessandria della Rocca
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2525749&APPID=8fbe995b2605abe6003ad5b588d1c19a
    67 City ID: 2978297 City: Saint-Martin-du-Mont
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2978297&APPID=8fbe995b2605abe6003ad5b588d1c19a
    68 City ID: 3203970 City: Blagaj
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3203970&APPID=8fbe995b2605abe6003ad5b588d1c19a
    69 City ID: 3107714 City: Torresmenudas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3107714&APPID=8fbe995b2605abe6003ad5b588d1c19a
    70 City ID: 2038283 City: Binzhou
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2038283&APPID=8fbe995b2605abe6003ad5b588d1c19a
    71 City ID: 671067 City: Pestera
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=671067&APPID=8fbe995b2605abe6003ad5b588d1c19a
    72 City ID: 3175720 City: Gualtieri
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3175720&APPID=8fbe995b2605abe6003ad5b588d1c19a
    73 City ID: 2974644 City: Seyssins
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2974644&APPID=8fbe995b2605abe6003ad5b588d1c19a
    74 City ID: 4161178 City: Lake Butler
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4161178&APPID=8fbe995b2605abe6003ad5b588d1c19a
    75 City ID: 495000 City: Shelkovskaya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=495000&APPID=8fbe995b2605abe6003ad5b588d1c19a
    76 City ID: 5114821 City: Delevan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5114821&APPID=8fbe995b2605abe6003ad5b588d1c19a
    77 City ID: 1253671 City: Usilampatti
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1253671&APPID=8fbe995b2605abe6003ad5b588d1c19a
    78 City ID: 5825424 City: Fort Washakie
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5825424&APPID=8fbe995b2605abe6003ad5b588d1c19a
    79 City ID: 2939307 City: Dalkendorf
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2939307&APPID=8fbe995b2605abe6003ad5b588d1c19a
    80 City ID: 4433016 City: Latimer
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4433016&APPID=8fbe995b2605abe6003ad5b588d1c19a
    81 City ID: 5869822 City: Nenana
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5869822&APPID=8fbe995b2605abe6003ad5b588d1c19a
    82 City ID: 2562815 City: Kirkop
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2562815&APPID=8fbe995b2605abe6003ad5b588d1c19a
    83 City ID: 5033911 City: Lake Sarah
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5033911&APPID=8fbe995b2605abe6003ad5b588d1c19a
    84 City ID: 7291921 City: Dundry
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7291921&APPID=8fbe995b2605abe6003ad5b588d1c19a
    85 City ID: 3056418 City: Adand
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3056418&APPID=8fbe995b2605abe6003ad5b588d1c19a
    86 City ID: 4158482 City: Hialeah Gardens
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4158482&APPID=8fbe995b2605abe6003ad5b588d1c19a
    87 City ID: 2658724 City: Schlieren
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2658724&APPID=8fbe995b2605abe6003ad5b588d1c19a
    88 City ID: 3069432 City: Nové Strakonice
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3069432&APPID=8fbe995b2605abe6003ad5b588d1c19a
    89 City ID: 5146055 City: Ashland
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5146055&APPID=8fbe995b2605abe6003ad5b588d1c19a
    90 City ID: 1817938 City: Anyi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1817938&APPID=8fbe995b2605abe6003ad5b588d1c19a
    91 City ID: 3947338 City: Arenal
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3947338&APPID=8fbe995b2605abe6003ad5b588d1c19a
    92 City ID: 74938 City: Hayfan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=74938&APPID=8fbe995b2605abe6003ad5b588d1c19a
    93 City ID: 3457991 City: Mangaratiba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3457991&APPID=8fbe995b2605abe6003ad5b588d1c19a
    94 City ID: 3169379 City: Rigolato
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3169379&APPID=8fbe995b2605abe6003ad5b588d1c19a
    95 City ID: 2899632 City: Holzleuten
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2899632&APPID=8fbe995b2605abe6003ad5b588d1c19a
    96 City ID: 4893472 City: Gardner
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4893472&APPID=8fbe995b2605abe6003ad5b588d1c19a
    97 City ID: 3601784 City: San Pedro de Tutule
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3601784&APPID=8fbe995b2605abe6003ad5b588d1c19a
    98 City ID: 3061321 City: Zulova
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3061321&APPID=8fbe995b2605abe6003ad5b588d1c19a
    99 City ID: 2973034 City: Teyjat
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2973034&APPID=8fbe995b2605abe6003ad5b588d1c19a
    100 City ID: 4462937 City: Dana
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4462937&APPID=8fbe995b2605abe6003ad5b588d1c19a
    101 City ID: 2803874 City: Zoschingen
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2803874&APPID=8fbe995b2605abe6003ad5b588d1c19a
    102 City ID: 665578 City: Tamadau Mare
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=665578&APPID=8fbe995b2605abe6003ad5b588d1c19a
    103 City ID: 805073 City: Starka
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=805073&APPID=8fbe995b2605abe6003ad5b588d1c19a
    104 City ID: 6445093 City: Saint-Didier
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6445093&APPID=8fbe995b2605abe6003ad5b588d1c19a
    105 City ID: 3221044 City: Landkreis Rotenburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3221044&APPID=8fbe995b2605abe6003ad5b588d1c19a
    106 City ID: 3124391 City: Cosuenda
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3124391&APPID=8fbe995b2605abe6003ad5b588d1c19a
    107 City ID: 3857756 City: El Maiten
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3857756&APPID=8fbe995b2605abe6003ad5b588d1c19a
    108 City ID: 3827219 City: Enthavi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3827219&APPID=8fbe995b2605abe6003ad5b588d1c19a
    109 City ID: 3076413 City: Driten
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3076413&APPID=8fbe995b2605abe6003ad5b588d1c19a
    110 City ID: 775890 City: Biskupiec
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=775890&APPID=8fbe995b2605abe6003ad5b588d1c19a
    111 City ID: 8030642 City: Puerto Bories
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=8030642&APPID=8fbe995b2605abe6003ad5b588d1c19a
    112 City ID: 2919652 City: Gnotzheim
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2919652&APPID=8fbe995b2605abe6003ad5b588d1c19a
    113 City ID: 2834652 City: Schwebheim
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2834652&APPID=8fbe995b2605abe6003ad5b588d1c19a
    114 City ID: 6355981 City: Salvaleón
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6355981&APPID=8fbe995b2605abe6003ad5b588d1c19a
    115 City ID: 6358704 City: Toreno
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6358704&APPID=8fbe995b2605abe6003ad5b588d1c19a
    116 City ID: 2695079 City: Lillsjönäs
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2695079&APPID=8fbe995b2605abe6003ad5b588d1c19a
    117 City ID: 1222662 City: Isfana
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1222662&APPID=8fbe995b2605abe6003ad5b588d1c19a
    118 City ID: 3389458 City: Santa Maria Velha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3389458&APPID=8fbe995b2605abe6003ad5b588d1c19a
    119 City ID: 674550 City: Ludesti
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=674550&APPID=8fbe995b2605abe6003ad5b588d1c19a
    120 City ID: 5120550 City: Heritage Hills
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5120550&APPID=8fbe995b2605abe6003ad5b588d1c19a
    121 City ID: 7871948 City: Himberg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7871948&APPID=8fbe995b2605abe6003ad5b588d1c19a
    122 City ID: 2916657 City: Großenbrach
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2916657&APPID=8fbe995b2605abe6003ad5b588d1c19a
    123 City ID: 5790172 City: Claquato
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5790172&APPID=8fbe995b2605abe6003ad5b588d1c19a
    124 City ID: 2920891 City: Gersthofen
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2920891&APPID=8fbe995b2605abe6003ad5b588d1c19a
    125 City ID: 3465745 City: Conceicao do Mato Dentro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3465745&APPID=8fbe995b2605abe6003ad5b588d1c19a
    126 City ID: 5345990 City: Eldridge
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5345990&APPID=8fbe995b2605abe6003ad5b588d1c19a
    127 City ID: 1649267 City: Belopa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1649267&APPID=8fbe995b2605abe6003ad5b588d1c19a
    128 City ID: 2782283 City: Atzbach
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2782283&APPID=8fbe995b2605abe6003ad5b588d1c19a
    129 City ID: 6447198 City: Barou-en-Auge
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6447198&APPID=8fbe995b2605abe6003ad5b588d1c19a
    130 City ID: 2848215 City: Rengsdorf
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2848215&APPID=8fbe995b2605abe6003ad5b588d1c19a
    131 City ID: 1548397 City: Shengci
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1548397&APPID=8fbe995b2605abe6003ad5b588d1c19a
    132 City ID: 8133978 City: Dimos Xylokastro-Evrostina
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=8133978&APPID=8fbe995b2605abe6003ad5b588d1c19a
    133 City ID: 4202308 City: Isle of Hope
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4202308&APPID=8fbe995b2605abe6003ad5b588d1c19a
    134 City ID: 1807468 City: Huanghua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1807468&APPID=8fbe995b2605abe6003ad5b588d1c19a
    135 City ID: 1263324 City: Mattur
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1263324&APPID=8fbe995b2605abe6003ad5b588d1c19a
    136 City ID: 3069844 City: Neratovice
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3069844&APPID=8fbe995b2605abe6003ad5b588d1c19a
    137 City ID: 3452029 City: Quijingue
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3452029&APPID=8fbe995b2605abe6003ad5b588d1c19a
    138 City ID: 3533117 City: Akil
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3533117&APPID=8fbe995b2605abe6003ad5b588d1c19a
    139 City ID: 2515158 City: Laujar de Andarax
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2515158&APPID=8fbe995b2605abe6003ad5b588d1c19a
    140 City ID: 757609 City: Swietajno
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=757609&APPID=8fbe995b2605abe6003ad5b588d1c19a
    141 City ID: 8010487 City: Lousã
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=8010487&APPID=8fbe995b2605abe6003ad5b588d1c19a
    142 City ID: 8012010 City: Loulé (São Sebastião)
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=8012010&APPID=8fbe995b2605abe6003ad5b588d1c19a
    143 City ID: 1814105 City: Dalang
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1814105&APPID=8fbe995b2605abe6003ad5b588d1c19a
    144 City ID: 7873358 City: Preding
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7873358&APPID=8fbe995b2605abe6003ad5b588d1c19a
    145 City ID: 2515672 City: La Parra
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2515672&APPID=8fbe995b2605abe6003ad5b588d1c19a
    146 City ID: 3111814 City: Ribaseca
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3111814&APPID=8fbe995b2605abe6003ad5b588d1c19a
    147 City ID: 1266452 City: Kizhake Chalakudi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1266452&APPID=8fbe995b2605abe6003ad5b588d1c19a
    148 City ID: 3928127 City: Departamento de Tacna
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3928127&APPID=8fbe995b2605abe6003ad5b588d1c19a
    149 City ID: 229268 City: Mbarara
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=229268&APPID=8fbe995b2605abe6003ad5b588d1c19a
    150 City ID: 569360 City: Cherdakly
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=569360&APPID=8fbe995b2605abe6003ad5b588d1c19a
    151 City ID: 743166 City: Kirklareli
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=743166&APPID=8fbe995b2605abe6003ad5b588d1c19a
    152 City ID: 7534560 City: Ilowo -Osada
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7534560&APPID=8fbe995b2605abe6003ad5b588d1c19a
    153 City ID: 4172052 City: Sanibel
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4172052&APPID=8fbe995b2605abe6003ad5b588d1c19a
    154 City ID: 703061 City: Lymanske
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=703061&APPID=8fbe995b2605abe6003ad5b588d1c19a
    155 City ID: 8185303 City: Sumberejo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=8185303&APPID=8fbe995b2605abe6003ad5b588d1c19a
    156 City ID: 6430985 City: Plomelin
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6430985&APPID=8fbe995b2605abe6003ad5b588d1c19a
    157 City ID: 609912 City: Ferrosplav
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=609912&APPID=8fbe995b2605abe6003ad5b588d1c19a
    158 City ID: 2522835 City: Ucria
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2522835&APPID=8fbe995b2605abe6003ad5b588d1c19a
    159 City ID: 3168389 City: San Felice sul Panaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3168389&APPID=8fbe995b2605abe6003ad5b588d1c19a
    160 City ID: 2020687 City: Luchki
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2020687&APPID=8fbe995b2605abe6003ad5b588d1c19a
    161 City ID: 6432767 City: Montreuil-sous-Pérouse
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6432767&APPID=8fbe995b2605abe6003ad5b588d1c19a
    162 City ID: 4719781 City: Plum Grove
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4719781&APPID=8fbe995b2605abe6003ad5b588d1c19a
    163 City ID: 963049 City: Rayton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=963049&APPID=8fbe995b2605abe6003ad5b588d1c19a
    164 City ID: 3470992 City: Bananal
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3470992&APPID=8fbe995b2605abe6003ad5b588d1c19a
    165 City ID: 1520061 City: Predgornoe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1520061&APPID=8fbe995b2605abe6003ad5b588d1c19a
    166 City ID: 6554383 City: Zeltingen-Rachtig
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6554383&APPID=8fbe995b2605abe6003ad5b588d1c19a
    167 City ID: 1261829 City: Narayangarh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1261829&APPID=8fbe995b2605abe6003ad5b588d1c19a
    168 City ID: 2899304 City: Hontheim
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2899304&APPID=8fbe995b2605abe6003ad5b588d1c19a
    169 City ID: 2076903 City: Beechina
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2076903&APPID=8fbe995b2605abe6003ad5b588d1c19a
    170 City ID: 8074780 City: Krojo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=8074780&APPID=8fbe995b2605abe6003ad5b588d1c19a
    171 City ID: 3388660 City: Sao Joao
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3388660&APPID=8fbe995b2605abe6003ad5b588d1c19a
    172 City ID: 6356575 City: Rubena
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6356575&APPID=8fbe995b2605abe6003ad5b588d1c19a
    173 City ID: 5043571 City: Rockville
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5043571&APPID=8fbe995b2605abe6003ad5b588d1c19a
    174 City ID: 3038393 City: Aire-sur-la-Lys
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3038393&APPID=8fbe995b2605abe6003ad5b588d1c19a
    175 City ID: 4924412 City: Ogden Dunes
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4924412&APPID=8fbe995b2605abe6003ad5b588d1c19a
    176 City ID: 3166808 City: Segrate
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3166808&APPID=8fbe995b2605abe6003ad5b588d1c19a
    177 City ID: 1917270 City: Boluo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1917270&APPID=8fbe995b2605abe6003ad5b588d1c19a
    178 City ID: 2347061 City: Sofo-Birnin-Gwari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2347061&APPID=8fbe995b2605abe6003ad5b588d1c19a
    179 City ID: 6608053 City: Volovoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6608053&APPID=8fbe995b2605abe6003ad5b588d1c19a
    180 City ID: 3025045 City: Chomerac
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3025045&APPID=8fbe995b2605abe6003ad5b588d1c19a
    181 City ID: 6554869 City: Ober-Flörsheim
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6554869&APPID=8fbe995b2605abe6003ad5b588d1c19a
    182 City ID: 655693 City: Jokioinen
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=655693&APPID=8fbe995b2605abe6003ad5b588d1c19a
    183 City ID: 2960011 City: Walsdorf
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2960011&APPID=8fbe995b2605abe6003ad5b588d1c19a
    184 City ID: 1856212 City: Naganohara
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1856212&APPID=8fbe995b2605abe6003ad5b588d1c19a
    185 City ID: 2172232 City: Carrajung
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2172232&APPID=8fbe995b2605abe6003ad5b588d1c19a
    186 City ID: 677160 City: Giroc
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=677160&APPID=8fbe995b2605abe6003ad5b588d1c19a
    187 City ID: 7873263 City: Redlham
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7873263&APPID=8fbe995b2605abe6003ad5b588d1c19a
    188 City ID: 3174397 City: Macchia Valfortore
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3174397&APPID=8fbe995b2605abe6003ad5b588d1c19a
    189 City ID: 2930941 City: Ellierode
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2930941&APPID=8fbe995b2605abe6003ad5b588d1c19a
    190 City ID: 6615881 City: Rousset
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6615881&APPID=8fbe995b2605abe6003ad5b588d1c19a
    191 City ID: 2967139 City: Zillisheim
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2967139&APPID=8fbe995b2605abe6003ad5b588d1c19a
    192 City ID: 3116758 City: Millaró
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3116758&APPID=8fbe995b2605abe6003ad5b588d1c19a
    193 City ID: 1794001 City: Songmuping
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1794001&APPID=8fbe995b2605abe6003ad5b588d1c19a
    194 City ID: 769106 City: Klembow
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=769106&APPID=8fbe995b2605abe6003ad5b588d1c19a
    195 City ID: 3169539 City: Recco
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3169539&APPID=8fbe995b2605abe6003ad5b588d1c19a
    196 City ID: 2660856 City: Escholzmatt
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2660856&APPID=8fbe995b2605abe6003ad5b588d1c19a
    197 City ID: 1863611 City: Godo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1863611&APPID=8fbe995b2605abe6003ad5b588d1c19a
    198 City ID: 1907972 City: Haodi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1907972&APPID=8fbe995b2605abe6003ad5b588d1c19a
    199 City ID: 2978369 City: Saint-Martin-de-Londres
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2978369&APPID=8fbe995b2605abe6003ad5b588d1c19a
    200 City ID: 2753174 City: Jutphaas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2753174&APPID=8fbe995b2605abe6003ad5b588d1c19a
    201 City ID: 3026612 City: Arrondissement de Charleville-Mézières
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3026612&APPID=8fbe995b2605abe6003ad5b588d1c19a
    202 City ID: 2906680 City: Helmstadt
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2906680&APPID=8fbe995b2605abe6003ad5b588d1c19a
    203 City ID: 6607759 City: Taynovo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6607759&APPID=8fbe995b2605abe6003ad5b588d1c19a
    204 City ID: 77515 City: Az Zaydiyah
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=77515&APPID=8fbe995b2605abe6003ad5b588d1c19a
    205 City ID: 2939905 City: Colmnitz
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2939905&APPID=8fbe995b2605abe6003ad5b588d1c19a
    206 City ID: 4971734 City: Medway
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4971734&APPID=8fbe995b2605abe6003ad5b588d1c19a
    207 City ID: 797411 City: Stepnoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=797411&APPID=8fbe995b2605abe6003ad5b588d1c19a
    208 City ID: 3194243 City: Obrovac
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3194243&APPID=8fbe995b2605abe6003ad5b588d1c19a
    209 City ID: 3170250 City: Pontelongo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3170250&APPID=8fbe995b2605abe6003ad5b588d1c19a
    210 City ID: 1803740 City: Lifuta
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1803740&APPID=8fbe995b2605abe6003ad5b588d1c19a
    211 City ID: 6556664 City: Schwarzenbach
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6556664&APPID=8fbe995b2605abe6003ad5b588d1c19a
    212 City ID: 6553339 City: Senscheid
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6553339&APPID=8fbe995b2605abe6003ad5b588d1c19a
    213 City ID: 5364059 City: La Presa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5364059&APPID=8fbe995b2605abe6003ad5b588d1c19a
    214 City ID: 4271918 City: Frontenac
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4271918&APPID=8fbe995b2605abe6003ad5b588d1c19a
    215 City ID: 3192224 City: Pula
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3192224&APPID=8fbe995b2605abe6003ad5b588d1c19a
    216 City ID: 2159374 City: Lucyvale
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2159374&APPID=8fbe995b2605abe6003ad5b588d1c19a
    217 City ID: 3130251 City: Alpens
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3130251&APPID=8fbe995b2605abe6003ad5b588d1c19a
    218 City ID: 5004776 City: Ovid
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5004776&APPID=8fbe995b2605abe6003ad5b588d1c19a
    219 City ID: 2814564 City: Wallichen
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2814564&APPID=8fbe995b2605abe6003ad5b588d1c19a
    220 City ID: 6957981 City: Zhuze
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6957981&APPID=8fbe995b2605abe6003ad5b588d1c19a
    221 City ID: 2403268 City: Towama
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2403268&APPID=8fbe995b2605abe6003ad5b588d1c19a
    222 City ID: 2523151 City: Serradifalco
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2523151&APPID=8fbe995b2605abe6003ad5b588d1c19a
    223 City ID: 3175453 City: Ischia Porto
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3175453&APPID=8fbe995b2605abe6003ad5b588d1c19a
    224 City ID: 3031402 City: Boubas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3031402&APPID=8fbe995b2605abe6003ad5b588d1c19a
    225 City ID: 3162412 City: Aure
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3162412&APPID=8fbe995b2605abe6003ad5b588d1c19a
    226 City ID: 3053199 City: Ersekvadkert
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3053199&APPID=8fbe995b2605abe6003ad5b588d1c19a
    227 City ID: 6693563 City: Región de Los Ríos
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6693563&APPID=8fbe995b2605abe6003ad5b588d1c19a
    228 City ID: 6443367 City: Notre-Dame-de-Bondeville
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6443367&APPID=8fbe995b2605abe6003ad5b588d1c19a
    229 City ID: 6115383 City: Quispamsis
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6115383&APPID=8fbe995b2605abe6003ad5b588d1c19a
    230 City ID: 3024681 City: Cleguerec
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3024681&APPID=8fbe995b2605abe6003ad5b588d1c19a
    231 City ID: 2942323 City: Buchholz in der Nordheide
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2942323&APPID=8fbe995b2605abe6003ad5b588d1c19a
    232 City ID: 3175458 City: Ischia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3175458&APPID=8fbe995b2605abe6003ad5b588d1c19a
    233 City ID: 523917 City: Mykanino
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=523917&APPID=8fbe995b2605abe6003ad5b588d1c19a
    234 City ID: 8197161 City: Kandangan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=8197161&APPID=8fbe995b2605abe6003ad5b588d1c19a
    235 City ID: 7511005 City: Moeiwadi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7511005&APPID=8fbe995b2605abe6003ad5b588d1c19a
    236 City ID: 2170547 City: Coominya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2170547&APPID=8fbe995b2605abe6003ad5b588d1c19a
    237 City ID: 732717 City: Byala Cherkva
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=732717&APPID=8fbe995b2605abe6003ad5b588d1c19a
    238 City ID: 545046 City: Kopylovo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=545046&APPID=8fbe995b2605abe6003ad5b588d1c19a
    239 City ID: 4561542 City: Strasburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4561542&APPID=8fbe995b2605abe6003ad5b588d1c19a
    240 City ID: 3217430 City: Ruda
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3217430&APPID=8fbe995b2605abe6003ad5b588d1c19a
    241 City ID: 3862338 City: Caspi Corral
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3862338&APPID=8fbe995b2605abe6003ad5b588d1c19a
    242 City ID: 2652818 City: Clive
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2652818&APPID=8fbe995b2605abe6003ad5b588d1c19a
    243 City ID: 2678265 City: Skanninge
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2678265&APPID=8fbe995b2605abe6003ad5b588d1c19a
    244 City ID: 6452199 City: Allas-les-Mines
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6452199&APPID=8fbe995b2605abe6003ad5b588d1c19a
    245 City ID: 4341715 City: Slagle
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4341715&APPID=8fbe995b2605abe6003ad5b588d1c19a
    246 City ID: 1673046 City: Laodian
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1673046&APPID=8fbe995b2605abe6003ad5b588d1c19a
    247 City ID: 2154669 City: Nyrang Creek
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2154669&APPID=8fbe995b2605abe6003ad5b588d1c19a
    248 City ID: 8013027 City: Fráguas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=8013027&APPID=8fbe995b2605abe6003ad5b588d1c19a
    249 City ID: 2657539 City: Alderton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2657539&APPID=8fbe995b2605abe6003ad5b588d1c19a
    250 City ID: 2733368 City: Tresouras
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2733368&APPID=8fbe995b2605abe6003ad5b588d1c19a
    251 City ID: 2796628 City: Hamois
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2796628&APPID=8fbe995b2605abe6003ad5b588d1c19a
    252 City ID: 7912120 City: Urug
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7912120&APPID=8fbe995b2605abe6003ad5b588d1c19a
    253 City ID: 8058378 City: Karangnongko
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=8058378&APPID=8fbe995b2605abe6003ad5b588d1c19a
    254 City ID: 6550512 City: Pölzig
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6550512&APPID=8fbe995b2605abe6003ad5b588d1c19a
    255 City ID: 2948164 City: Bitterfeld
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2948164&APPID=8fbe995b2605abe6003ad5b588d1c19a
    256 City ID: 487837 City: Stavrovo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=487837&APPID=8fbe995b2605abe6003ad5b588d1c19a
    257 City ID: 4003923 City: Jiquilpan de Juarez
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4003923&APPID=8fbe995b2605abe6003ad5b588d1c19a
    258 City ID: 6361991 City: Foios
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6361991&APPID=8fbe995b2605abe6003ad5b588d1c19a
    259 City ID: 1722947 City: Bulasa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1722947&APPID=8fbe995b2605abe6003ad5b588d1c19a
    260 City ID: 3117256 City: Masía de la Lloma
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3117256&APPID=8fbe995b2605abe6003ad5b588d1c19a
    261 City ID: 4608615 City: Brighton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4608615&APPID=8fbe995b2605abe6003ad5b588d1c19a
    262 City ID: 1640354 City: Kencong
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1640354&APPID=8fbe995b2605abe6003ad5b588d1c19a
    263 City ID: 6433909 City: Oeyregave
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6433909&APPID=8fbe995b2605abe6003ad5b588d1c19a
    264 City ID: 5145730 City: Amoy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5145730&APPID=8fbe995b2605abe6003ad5b588d1c19a
    265 City ID: 6356751 City: Casas del Castañar
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6356751&APPID=8fbe995b2605abe6003ad5b588d1c19a
    266 City ID: 2940157 City: Charlottenhof
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2940157&APPID=8fbe995b2605abe6003ad5b588d1c19a
    267 City ID: 2788448 City: Quévy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2788448&APPID=8fbe995b2605abe6003ad5b588d1c19a
    268 City ID: 7287088 City: Schlatt-Haslen
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7287088&APPID=8fbe995b2605abe6003ad5b588d1c19a
    269 City ID: 1728415 City: Balas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1728415&APPID=8fbe995b2605abe6003ad5b588d1c19a
    270 City ID: 1806466 City: Guangyuan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1806466&APPID=8fbe995b2605abe6003ad5b588d1c19a
    271 City ID: 2173049 City: Burren Junction
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2173049&APPID=8fbe995b2605abe6003ad5b588d1c19a
    272 City ID: 7839184 City: Makata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7839184&APPID=8fbe995b2605abe6003ad5b588d1c19a
    273 City ID: 2188371 City: Lincoln
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2188371&APPID=8fbe995b2605abe6003ad5b588d1c19a
    274 City ID: 3121796 City: Fustinana
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3121796&APPID=8fbe995b2605abe6003ad5b588d1c19a
    275 City ID: 3629653 City: Puerto Piritu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3629653&APPID=8fbe995b2605abe6003ad5b588d1c19a
    276 City ID: 3023477 City: Cosnes-et-Romain
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3023477&APPID=8fbe995b2605abe6003ad5b588d1c19a
    277 City ID: 3128297 City: Benasal
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3128297&APPID=8fbe995b2605abe6003ad5b588d1c19a
    278 City ID: 2851175 City: Raben Steinfeld
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2851175&APPID=8fbe995b2605abe6003ad5b588d1c19a
    279 City ID: 1796647 City: Sanqiao
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1796647&APPID=8fbe995b2605abe6003ad5b588d1c19a
    280 City ID: 4271901 City: Galena
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4271901&APPID=8fbe995b2605abe6003ad5b588d1c19a
    281 City ID: 5990415 City: Kelligrews
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5990415&APPID=8fbe995b2605abe6003ad5b588d1c19a
    282 City ID: 3024939 City: Cinq-Cantons
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3024939&APPID=8fbe995b2605abe6003ad5b588d1c19a
    283 City ID: 3182477 City: Baiso
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3182477&APPID=8fbe995b2605abe6003ad5b588d1c19a
    284 City ID: 1680344 City: Umabay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1680344&APPID=8fbe995b2605abe6003ad5b588d1c19a
    285 City ID: 2813864 City: Wasbek
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2813864&APPID=8fbe995b2605abe6003ad5b588d1c19a
    286 City ID: 2980611 City: Sainte-Fereole
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2980611&APPID=8fbe995b2605abe6003ad5b588d1c19a
    287 City ID: 736762 City: Aravissos
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=736762&APPID=8fbe995b2605abe6003ad5b588d1c19a
    288 City ID: 2977072 City: Saint-Saturnin
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2977072&APPID=8fbe995b2605abe6003ad5b588d1c19a
    289 City ID: 2828140 City: Steinfeld
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2828140&APPID=8fbe995b2605abe6003ad5b588d1c19a
    290 City ID: 1276321 City: Bhadravati
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1276321&APPID=8fbe995b2605abe6003ad5b588d1c19a
    291 City ID: 6291334 City: Hohenbühl/Bubenholz
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6291334&APPID=8fbe995b2605abe6003ad5b588d1c19a
    292 City ID: 2396926 City: Province de l’ Ogooué-Ivindo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2396926&APPID=8fbe995b2605abe6003ad5b588d1c19a
    293 City ID: 2885231 City: Kothendorf
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2885231&APPID=8fbe995b2605abe6003ad5b588d1c19a
    294 City ID: 3124188 City: Cubillas de Cerrato
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3124188&APPID=8fbe995b2605abe6003ad5b588d1c19a
    295 City ID: 4345555 City: Watson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4345555&APPID=8fbe995b2605abe6003ad5b588d1c19a
    296 City ID: 2871128 City: Mildstedthof
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2871128&APPID=8fbe995b2605abe6003ad5b588d1c19a
    297 City ID: 3314176 City: Clogh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3314176&APPID=8fbe995b2605abe6003ad5b588d1c19a
    298 City ID: 3002958 City: Le Perron
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3002958&APPID=8fbe995b2605abe6003ad5b588d1c19a
    299 City ID: 2886301 City: Kollmarsreute
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2886301&APPID=8fbe995b2605abe6003ad5b588d1c19a
    300 City ID: 2635927 City: Three Legged Cross
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2635927&APPID=8fbe995b2605abe6003ad5b588d1c19a
    301 City ID: 6362810 City: Godojos
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6362810&APPID=8fbe995b2605abe6003ad5b588d1c19a
    302 City ID: 6552522 City: Eystrup
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6552522&APPID=8fbe995b2605abe6003ad5b588d1c19a
    303 City ID: 1262151 City: Nahan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1262151&APPID=8fbe995b2605abe6003ad5b588d1c19a
    304 City ID: 5767488 City: North Eagle Butte
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5767488&APPID=8fbe995b2605abe6003ad5b588d1c19a
    305 City ID: 4360713 City: Linthicum
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4360713&APPID=8fbe995b2605abe6003ad5b588d1c19a
    306 City ID: 6693294 City: Nommern
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6693294&APPID=8fbe995b2605abe6003ad5b588d1c19a
    307 City ID: 1662615 City: Ban Lao
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1662615&APPID=8fbe995b2605abe6003ad5b588d1c19a
    308 City ID: 530397 City: Mal'tsev
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=530397&APPID=8fbe995b2605abe6003ad5b588d1c19a
    309 City ID: 1803944 City: Liangyaping
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1803944&APPID=8fbe995b2605abe6003ad5b588d1c19a
    310 City ID: 2966834 City: Attanagh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2966834&APPID=8fbe995b2605abe6003ad5b588d1c19a
    311 City ID: 731549 City: Gabrovo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=731549&APPID=8fbe995b2605abe6003ad5b588d1c19a
    312 City ID: 696309 City: Prigorodnoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=696309&APPID=8fbe995b2605abe6003ad5b588d1c19a
    313 City ID: 2815800 City: Waalhaupten
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2815800&APPID=8fbe995b2605abe6003ad5b588d1c19a
    314 City ID: 2962363 City: Mullinahone
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2962363&APPID=8fbe995b2605abe6003ad5b588d1c19a
    315 City ID: 711055 City: Buzovaya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=711055&APPID=8fbe995b2605abe6003ad5b588d1c19a
    316 City ID: 2523699 City: Portoscuso
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2523699&APPID=8fbe995b2605abe6003ad5b588d1c19a
    317 City ID: 2997497 City: Loubens
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2997497&APPID=8fbe995b2605abe6003ad5b588d1c19a
    318 City ID: 1137247 City: Khamyab
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1137247&APPID=8fbe995b2605abe6003ad5b588d1c19a
    319 City ID: 6552283 City: Nienwohld
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6552283&APPID=8fbe995b2605abe6003ad5b588d1c19a
    320 City ID: 1607552 City: Phrae
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1607552&APPID=8fbe995b2605abe6003ad5b588d1c19a
    321 City ID: 1815035 City: Chexi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1815035&APPID=8fbe995b2605abe6003ad5b588d1c19a
    322 City ID: 3035065 City: Baraqueville
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3035065&APPID=8fbe995b2605abe6003ad5b588d1c19a
    323 City ID: 4317656 City: Boston
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4317656&APPID=8fbe995b2605abe6003ad5b588d1c19a
    324 City ID: 3928274 City: Supe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3928274&APPID=8fbe995b2605abe6003ad5b588d1c19a
    325 City ID: 6360274 City: Aldealengua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6360274&APPID=8fbe995b2605abe6003ad5b588d1c19a
    326 City ID: 7873507 City: Selzthal
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7873507&APPID=8fbe995b2605abe6003ad5b588d1c19a
    327 City ID: 4736982 City: Titus County
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4736982&APPID=8fbe995b2605abe6003ad5b588d1c19a
    328 City ID: 6437567 City: Hanviller
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6437567&APPID=8fbe995b2605abe6003ad5b588d1c19a
    329 City ID: 3120506 City: Hueva
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3120506&APPID=8fbe995b2605abe6003ad5b588d1c19a
    330 City ID: 2652518 City: Colwall
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2652518&APPID=8fbe995b2605abe6003ad5b588d1c19a
    331 City ID: 6548087 City: Priborn
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6548087&APPID=8fbe995b2605abe6003ad5b588d1c19a
    332 City ID: 6434451 City: Sanssac-l'Église
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6434451&APPID=8fbe995b2605abe6003ad5b588d1c19a
    333 City ID: 3353715 City: Outjo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3353715&APPID=8fbe995b2605abe6003ad5b588d1c19a
    334 City ID: 5054390 City: Canton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5054390&APPID=8fbe995b2605abe6003ad5b588d1c19a
    335 City ID: 4987112 City: Brown City
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4987112&APPID=8fbe995b2605abe6003ad5b588d1c19a
    336 City ID: 588157 City: Turba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=588157&APPID=8fbe995b2605abe6003ad5b588d1c19a
    337 City ID: 3013011 City: Huismes
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3013011&APPID=8fbe995b2605abe6003ad5b588d1c19a
    338 City ID: 6534810 City: Africo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6534810&APPID=8fbe995b2605abe6003ad5b588d1c19a
    339 City ID: 921756 City: Mtsamdou
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=921756&APPID=8fbe995b2605abe6003ad5b588d1c19a
    340 City ID: 2931424 City: Eisingen
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2931424&APPID=8fbe995b2605abe6003ad5b588d1c19a
    341 City ID: 3129250 City: Aspuru
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3129250&APPID=8fbe995b2605abe6003ad5b588d1c19a
    342 City ID: 1726000 City: Batutitik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1726000&APPID=8fbe995b2605abe6003ad5b588d1c19a
    343 City ID: 4924243 City: North Liberty
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4924243&APPID=8fbe995b2605abe6003ad5b588d1c19a
    344 City ID: 6429231 City: Moutier-Malcard
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6429231&APPID=8fbe995b2605abe6003ad5b588d1c19a
    345 City ID: 1185270 City: Bandarban
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1185270&APPID=8fbe995b2605abe6003ad5b588d1c19a
    346 City ID: 672620 City: Murfatlar
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=672620&APPID=8fbe995b2605abe6003ad5b588d1c19a
    347 City ID: 2463951 City: Zawiyat al Jadidi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2463951&APPID=8fbe995b2605abe6003ad5b588d1c19a
    348 City ID: 2916954 City: Grossbockedra
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2916954&APPID=8fbe995b2605abe6003ad5b588d1c19a
    349 City ID: 5157675 City: Hiram
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5157675&APPID=8fbe995b2605abe6003ad5b588d1c19a
    350 City ID: 3079685 City: Bakov nad Jizerou
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3079685&APPID=8fbe995b2605abe6003ad5b588d1c19a
    351 City ID: 3171136 City: Pescocostanzo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3171136&APPID=8fbe995b2605abe6003ad5b588d1c19a
    352 City ID: 1796172 City: Shangling
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1796172&APPID=8fbe995b2605abe6003ad5b588d1c19a
    353 City ID: 5570065 City: Red Bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5570065&APPID=8fbe995b2605abe6003ad5b588d1c19a
    354 City ID: 6138472 City: Saint-Jean-de-Matha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6138472&APPID=8fbe995b2605abe6003ad5b588d1c19a
    355 City ID: 2754635 City: Heesch
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2754635&APPID=8fbe995b2605abe6003ad5b588d1c19a
    356 City ID: 1147586 City: Bāgh-e Bālinah
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1147586&APPID=8fbe995b2605abe6003ad5b588d1c19a
    357 City ID: 1700667 City: Masinloc
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1700667&APPID=8fbe995b2605abe6003ad5b588d1c19a
    358 City ID: 7873667 City: Pians
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7873667&APPID=8fbe995b2605abe6003ad5b588d1c19a
    359 City ID: 6692234 City: Potos (Thassos)
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6692234&APPID=8fbe995b2605abe6003ad5b588d1c19a
    360 City ID: 1863356 City: Hakonegasaki
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1863356&APPID=8fbe995b2605abe6003ad5b588d1c19a
    361 City ID: 7872955 City: Falkenstein
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7872955&APPID=8fbe995b2605abe6003ad5b588d1c19a
    362 City ID: 3111322 City: Royuela de Rio Franco
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3111322&APPID=8fbe995b2605abe6003ad5b588d1c19a
    363 City ID: 2520214 City: Cantoblanco
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2520214&APPID=8fbe995b2605abe6003ad5b588d1c19a
    364 City ID: 2152668 City: Portland
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2152668&APPID=8fbe995b2605abe6003ad5b588d1c19a
    365 City ID: 6443797 City: Pomponne
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6443797&APPID=8fbe995b2605abe6003ad5b588d1c19a
    366 City ID: 3177684 City: Cupramontana
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3177684&APPID=8fbe995b2605abe6003ad5b588d1c19a
    367 City ID: 3531604 City: Capula
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3531604&APPID=8fbe995b2605abe6003ad5b588d1c19a
    368 City ID: 3456998 City: Mogi Mirim
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3456998&APPID=8fbe995b2605abe6003ad5b588d1c19a
    369 City ID: 2521510 City: Aspe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2521510&APPID=8fbe995b2605abe6003ad5b588d1c19a
    370 City ID: 7873435 City: Rohrbach an der Lafnitz
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7873435&APPID=8fbe995b2605abe6003ad5b588d1c19a
    371 City ID: 3570392 City: Le Vauclin
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3570392&APPID=8fbe995b2605abe6003ad5b588d1c19a
    372 City ID: 164947 City: Salamiyah
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=164947&APPID=8fbe995b2605abe6003ad5b588d1c19a
    373 City ID: 757531 City: Sypniewo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=757531&APPID=8fbe995b2605abe6003ad5b588d1c19a
    374 City ID: 1606687 City: Sam Khok
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1606687&APPID=8fbe995b2605abe6003ad5b588d1c19a
    375 City ID: 6554835 City: Dintesheim
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6554835&APPID=8fbe995b2605abe6003ad5b588d1c19a
    376 City ID: 3009494 City: La Ferte-Bernard
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3009494&APPID=8fbe995b2605abe6003ad5b588d1c19a
    377 City ID: 2864131 City: Neusorg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2864131&APPID=8fbe995b2605abe6003ad5b588d1c19a
    378 City ID: 3010724 City: La Brugère
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3010724&APPID=8fbe995b2605abe6003ad5b588d1c19a
    379 City ID: 3031420 City: Botmel
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3031420&APPID=8fbe995b2605abe6003ad5b588d1c19a
    380 City ID: 517668 City: Novoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=517668&APPID=8fbe995b2605abe6003ad5b588d1c19a
    381 City ID: 3172941 City: Montefalco
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3172941&APPID=8fbe995b2605abe6003ad5b588d1c19a
    382 City ID: 1646227 City: Cipicung
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1646227&APPID=8fbe995b2605abe6003ad5b588d1c19a
    383 City ID: 3129697 City: Areas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3129697&APPID=8fbe995b2605abe6003ad5b588d1c19a
    384 City ID: 2980102 City: Arrondissement de Saint-Flour
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2980102&APPID=8fbe995b2605abe6003ad5b588d1c19a
    385 City ID: 2654660 City: Brixworth
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2654660&APPID=8fbe995b2605abe6003ad5b588d1c19a
    386 City ID: 6357402 City: Canalejas del Arroyo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6357402&APPID=8fbe995b2605abe6003ad5b588d1c19a
    387 City ID: 789600 City: Kanjiza
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=789600&APPID=8fbe995b2605abe6003ad5b588d1c19a
    388 City ID: 1684191 City: Takub
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1684191&APPID=8fbe995b2605abe6003ad5b588d1c19a
    389 City ID: 2980980 City: Saint-Cyprien
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2980980&APPID=8fbe995b2605abe6003ad5b588d1c19a
    390 City ID: 1292288 City: Thaton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1292288&APPID=8fbe995b2605abe6003ad5b588d1c19a
    391 City ID: 3032440 City: Blaison-Gohier
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3032440&APPID=8fbe995b2605abe6003ad5b588d1c19a
    392 City ID: 6137758 City: Sainte-Barbe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6137758&APPID=8fbe995b2605abe6003ad5b588d1c19a
    393 City ID: 2521368 City: Balsa de Ves
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2521368&APPID=8fbe995b2605abe6003ad5b588d1c19a
    394 City ID: 6452022 City: Joinville-le-Pont
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6452022&APPID=8fbe995b2605abe6003ad5b588d1c19a
    395 City ID: 2735080 City: Rio Torto
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2735080&APPID=8fbe995b2605abe6003ad5b588d1c19a
    396 City ID: 8010237 City: Banachaur
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=8010237&APPID=8fbe995b2605abe6003ad5b588d1c19a
    397 City ID: 5265518 City: Oconto County
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5265518&APPID=8fbe995b2605abe6003ad5b588d1c19a
    398 City ID: 1835967 City: Jenzan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1835967&APPID=8fbe995b2605abe6003ad5b588d1c19a
    399 City ID: 5373504 City: Mira Monte
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5373504&APPID=8fbe995b2605abe6003ad5b588d1c19a
    400 City ID: 2023117 City: Karpovo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2023117&APPID=8fbe995b2605abe6003ad5b588d1c19a
    401 City ID: 1714163 City: Dumanjog
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1714163&APPID=8fbe995b2605abe6003ad5b588d1c19a
    402 City ID: 2865691 City: Neuenhaus
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2865691&APPID=8fbe995b2605abe6003ad5b588d1c19a
    403 City ID: 3063112 City: Veltruby
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3063112&APPID=8fbe995b2605abe6003ad5b588d1c19a
    404 City ID: 788040 City: Melenci
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=788040&APPID=8fbe995b2605abe6003ad5b588d1c19a
    405 City ID: 6355627 City: Arenas de San Pedro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6355627&APPID=8fbe995b2605abe6003ad5b588d1c19a
    406 City ID: 592276 City: Emmaste
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=592276&APPID=8fbe995b2605abe6003ad5b588d1c19a
    407 City ID: 2549626 City: El Menzeh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2549626&APPID=8fbe995b2605abe6003ad5b588d1c19a
    408 City ID: 6553693 City: Illerich
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6553693&APPID=8fbe995b2605abe6003ad5b588d1c19a
    409 City ID: 2663036 City: Viken
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2663036&APPID=8fbe995b2605abe6003ad5b588d1c19a
    410 City ID: 4458175 City: Burgaw
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4458175&APPID=8fbe995b2605abe6003ad5b588d1c19a
    411 City ID: 1166062 City: Sarai Sidhu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1166062&APPID=8fbe995b2605abe6003ad5b588d1c19a
    412 City ID: 2234353 City: Besongabang
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2234353&APPID=8fbe995b2605abe6003ad5b588d1c19a
    413 City ID: 2797598 City: Gerpinnes
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2797598&APPID=8fbe995b2605abe6003ad5b588d1c19a
    414 City ID: 673096 City: Miroslavesti
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=673096&APPID=8fbe995b2605abe6003ad5b588d1c19a
    415 City ID: 2892307 City: Katterbach
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2892307&APPID=8fbe995b2605abe6003ad5b588d1c19a
    416 City ID: 265560 City: Agrinio
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=265560&APPID=8fbe995b2605abe6003ad5b588d1c19a
    417 City ID: 2882695 City: Kühr
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2882695&APPID=8fbe995b2605abe6003ad5b588d1c19a
    418 City ID: 2852404 City: Pötzmes
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2852404&APPID=8fbe995b2605abe6003ad5b588d1c19a
    419 City ID: 284890 City: Ar Ram wa Dahiyat al Barid
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=284890&APPID=8fbe995b2605abe6003ad5b588d1c19a
    420 City ID: 2755203 City: Gemeente Grootegast
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2755203&APPID=8fbe995b2605abe6003ad5b588d1c19a
    421 City ID: 2518820 City: Don Benito
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2518820&APPID=8fbe995b2605abe6003ad5b588d1c19a
    422 City ID: 3675808 City: Mabobo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3675808&APPID=8fbe995b2605abe6003ad5b588d1c19a
    423 City ID: 1611461 City: Buntharik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1611461&APPID=8fbe995b2605abe6003ad5b588d1c19a
    424 City ID: 2878484 City: Lessien
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2878484&APPID=8fbe995b2605abe6003ad5b588d1c19a
    425 City ID: 862944 City: Icmeler
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=862944&APPID=8fbe995b2605abe6003ad5b588d1c19a
    426 City ID: 6356498 City: Miraveche
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6356498&APPID=8fbe995b2605abe6003ad5b588d1c19a
    427 City ID: 1912205 City: Ungsang
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1912205&APPID=8fbe995b2605abe6003ad5b588d1c19a
    428 City ID: 6548421 City: Lohme
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6548421&APPID=8fbe995b2605abe6003ad5b588d1c19a
    429 City ID: 3110110 City: Sant Pol de Mar
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3110110&APPID=8fbe995b2605abe6003ad5b588d1c19a
    430 City ID: 1851348 City: Suzuka
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1851348&APPID=8fbe995b2605abe6003ad5b588d1c19a
    431 City ID: 6556692 City: Sünching
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6556692&APPID=8fbe995b2605abe6003ad5b588d1c19a
    432 City ID: 692749 City: Stari Bohorodchany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=692749&APPID=8fbe995b2605abe6003ad5b588d1c19a
    433 City ID: 3084107 City: Swiatniki Gorne
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3084107&APPID=8fbe995b2605abe6003ad5b588d1c19a
    434 City ID: 6439165 City: Monnai
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6439165&APPID=8fbe995b2605abe6003ad5b588d1c19a
    435 City ID: 6551525 City: Alkersum
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6551525&APPID=8fbe995b2605abe6003ad5b588d1c19a
    436 City ID: 4576268 City: Dalzell
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4576268&APPID=8fbe995b2605abe6003ad5b588d1c19a
    437 City ID: 6557120 City: Ried
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6557120&APPID=8fbe995b2605abe6003ad5b588d1c19a
    438 City ID: 2876904 City: Lipperode
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2876904&APPID=8fbe995b2605abe6003ad5b588d1c19a
    439 City ID: 2847231 City: Riedenburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2847231&APPID=8fbe995b2605abe6003ad5b588d1c19a
    440 City ID: 765639 City: Jeziorzany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=765639&APPID=8fbe995b2605abe6003ad5b588d1c19a
    441 City ID: 3076586 City: Okres Domažlice
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3076586&APPID=8fbe995b2605abe6003ad5b588d1c19a
    442 City ID: 5972815 City: Hayward Cove
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=5972815&APPID=8fbe995b2605abe6003ad5b588d1c19a
    443 City ID: 2983283 City: Roche-en-Régnier
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2983283&APPID=8fbe995b2605abe6003ad5b588d1c19a
    444 City ID: 6434524 City: Sainte-Luce-sur-Loire
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6434524&APPID=8fbe995b2605abe6003ad5b588d1c19a
    445 City ID: 6553242 City: Dipperz
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6553242&APPID=8fbe995b2605abe6003ad5b588d1c19a
    446 City ID: 8135343 City: Erdu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=8135343&APPID=8fbe995b2605abe6003ad5b588d1c19a
    447 City ID: 6360087 City: Poza de la Vega
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6360087&APPID=8fbe995b2605abe6003ad5b588d1c19a
    448 City ID: 3617388 City: Palacaguina
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3617388&APPID=8fbe995b2605abe6003ad5b588d1c19a
    449 City ID: 677672 City: Galbinasi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=677672&APPID=8fbe995b2605abe6003ad5b588d1c19a
    450 City ID: 6557396 City: Barsinghausen, Stadt
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6557396&APPID=8fbe995b2605abe6003ad5b588d1c19a
    451 City ID: 6447298 City: Angoulême
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6447298&APPID=8fbe995b2605abe6003ad5b588d1c19a
    452 City ID: 2523608 City: Rizziconi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2523608&APPID=8fbe995b2605abe6003ad5b588d1c19a
    453 City ID: 2659136 City: Prilly
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2659136&APPID=8fbe995b2605abe6003ad5b588d1c19a
    454 City ID: 294952 City: Southern District
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=294952&APPID=8fbe995b2605abe6003ad5b588d1c19a
    455 City ID: 3013779 City: Hautefaye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3013779&APPID=8fbe995b2605abe6003ad5b588d1c19a
    456 City ID: 77985 City: Ash Shaghadirah
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=77985&APPID=8fbe995b2605abe6003ad5b588d1c19a
    457 City ID: 2813641 City: Wattendorf
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2813641&APPID=8fbe995b2605abe6003ad5b588d1c19a
    458 City ID: 1699204 City: Morong
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1699204&APPID=8fbe995b2605abe6003ad5b588d1c19a
    459 City ID: 3014027 City: Hamars
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3014027&APPID=8fbe995b2605abe6003ad5b588d1c19a
    460 City ID: 4007424 City: El Tajito
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4007424&APPID=8fbe995b2605abe6003ad5b588d1c19a
    461 City ID: 2894977 City: Jesenwang
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2894977&APPID=8fbe995b2605abe6003ad5b588d1c19a
    462 City ID: 6554155 City: Mogendorf
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6554155&APPID=8fbe995b2605abe6003ad5b588d1c19a
    463 City ID: 320835 City: Bostanci
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=320835&APPID=8fbe995b2605abe6003ad5b588d1c19a
    464 City ID: 3169131 City: Rocca Sinibalda
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3169131&APPID=8fbe995b2605abe6003ad5b588d1c19a
    465 City ID: 3981069 City: Tres Palos
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3981069&APPID=8fbe995b2605abe6003ad5b588d1c19a
    466 City ID: 2986733 City: Ploemel
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2986733&APPID=8fbe995b2605abe6003ad5b588d1c19a
    467 City ID: 6110611 City: Pont Rouge
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6110611&APPID=8fbe995b2605abe6003ad5b588d1c19a
    468 City ID: 7783146 City: Cempaka
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=7783146&APPID=8fbe995b2605abe6003ad5b588d1c19a
    469 City ID: 2635563 City: Tranent
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2635563&APPID=8fbe995b2605abe6003ad5b588d1c19a
    470 City ID: 1279394 City: Abu Road
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1279394&APPID=8fbe995b2605abe6003ad5b588d1c19a
    471 City ID: 2948052 City: Blankenhof
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2948052&APPID=8fbe995b2605abe6003ad5b588d1c19a
    472 City ID: 4072156 City: Leesburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4072156&APPID=8fbe995b2605abe6003ad5b588d1c19a
    473 City ID: 8058308 City: Tlogoharum
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=8058308&APPID=8fbe995b2605abe6003ad5b588d1c19a
    474 City ID: 6362302 City: Valdearcos de la Vega
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6362302&APPID=8fbe995b2605abe6003ad5b588d1c19a
    475 City ID: 3452992 City: Porecatu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3452992&APPID=8fbe995b2605abe6003ad5b588d1c19a
    476 City ID: 2979276 City: Saint-Jean-d'Estissac
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2979276&APPID=8fbe995b2605abe6003ad5b588d1c19a
    477 City ID: 3711240 City: El Cano
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3711240&APPID=8fbe995b2605abe6003ad5b588d1c19a
    478 City ID: 658224 City: Helsinki
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=658224&APPID=8fbe995b2605abe6003ad5b588d1c19a
    479 City ID: 703142 City: Letychiv
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=703142&APPID=8fbe995b2605abe6003ad5b588d1c19a
    480 City ID: 1917490 City: Dengfang
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1917490&APPID=8fbe995b2605abe6003ad5b588d1c19a
    481 City ID: 3466913 City: Carmo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3466913&APPID=8fbe995b2605abe6003ad5b588d1c19a
    482 City ID: 6556759 City: Glashütten
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=6556759&APPID=8fbe995b2605abe6003ad5b588d1c19a
    483 City ID: 2140471 City: La Coulée
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2140471&APPID=8fbe995b2605abe6003ad5b588d1c19a
    484 City ID: 4866066 City: Manson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4866066&APPID=8fbe995b2605abe6003ad5b588d1c19a
    485 City ID: 3456579 City: Muliterno
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3456579&APPID=8fbe995b2605abe6003ad5b588d1c19a
    486 City ID: 2647723 City: Gwyddelwern
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2647723&APPID=8fbe995b2605abe6003ad5b588d1c19a
    487 City ID: 2565056 City: Punta Umbria
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2565056&APPID=8fbe995b2605abe6003ad5b588d1c19a
    488 City ID: 1807653 City: Huaiya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1807653&APPID=8fbe995b2605abe6003ad5b588d1c19a
    489 City ID: 1796883 City: Sangke
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1796883&APPID=8fbe995b2605abe6003ad5b588d1c19a
    490 City ID: 4901730 City: McLean County
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=4901730&APPID=8fbe995b2605abe6003ad5b588d1c19a
    491 City ID: 1129636 City: Qarchi Gak
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1129636&APPID=8fbe995b2605abe6003ad5b588d1c19a
    492 City ID: 2076213 City: Bolgart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2076213&APPID=8fbe995b2605abe6003ad5b588d1c19a
    493 City ID: 3051294 City: Hosszúhát
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3051294&APPID=8fbe995b2605abe6003ad5b588d1c19a
    494 City ID: 2852244 City: Premberg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2852244&APPID=8fbe995b2605abe6003ad5b588d1c19a
    495 City ID: 1254420 City: Tiptur
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1254420&APPID=8fbe995b2605abe6003ad5b588d1c19a
    496 City ID: 733700 City: Aleko-Konstantinovo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=733700&APPID=8fbe995b2605abe6003ad5b588d1c19a
    497 City ID: 1264829 City: Loharu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=1264829&APPID=8fbe995b2605abe6003ad5b588d1c19a
    498 City ID: 3427602 City: Turdera
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3427602&APPID=8fbe995b2605abe6003ad5b588d1c19a
    499 City ID: 2869751 City: Monsheim
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=2869751&APPID=8fbe995b2605abe6003ad5b588d1c19a
    500 City ID: 3039676 City: Parròquia d'Ordino
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&id=3039676&APPID=8fbe995b2605abe6003ad5b588d1c19a



```python
weather_data = {"Date": date_data, "Country": country_data, "City": cities, "Lat": lat_data, "Lng": lon_data, "Max Temp": temp_data, "Humidity": humidity_data, 
                "Cloudiness": cloudiness_data, "Wind Speed": windspeed_data}
weather_data = pd.DataFrame(weather_data)

#save weather data to CSV
weather_data.to_csv("CityWeatherData_New.csv", index=False)
```


```python
weather_data.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>City</th>
      <th>Cloudiness</th>
      <th>Country</th>
      <th>Date</th>
      <th>Humidity</th>
      <th>Lat</th>
      <th>Lng</th>
      <th>Max Temp</th>
      <th>Wind Speed</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>County Donegal</td>
      <td>76</td>
      <td>IE</td>
      <td>1513658168</td>
      <td>92</td>
      <td>54.92</td>
      <td>-8.00</td>
      <td>51.09</td>
      <td>18.37</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Sant Quirze Safaja</td>
      <td>0</td>
      <td>ES</td>
      <td>1513657800</td>
      <td>100</td>
      <td>41.73</td>
      <td>2.18</td>
      <td>41.00</td>
      <td>3.36</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Fuentelcesped</td>
      <td>0</td>
      <td>ES</td>
      <td>1513658169</td>
      <td>90</td>
      <td>41.59</td>
      <td>-3.64</td>
      <td>29.58</td>
      <td>6.73</td>
    </tr>
    <tr>
      <th>3</th>
      <td>San Ferdinando</td>
      <td>40</td>
      <td>IT</td>
      <td>1513655700</td>
      <td>61</td>
      <td>38.49</td>
      <td>15.92</td>
      <td>48.20</td>
      <td>8.05</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Castiglione Olona</td>
      <td>0</td>
      <td>IT</td>
      <td>1513655400</td>
      <td>85</td>
      <td>45.75</td>
      <td>8.87</td>
      <td>28.40</td>
      <td>6.93</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Build a scatter plot for each data type 
#Temperature (F) vs. Latitude

plt.scatter(lat_data, temp_data, marker="o")

# Incorporate the other graph properties
plt.title("Latitude in World Cities vs. Max Temperature (F)")
plt.ylabel("Temperature")
plt.xlabel("Latitude")
plt.grid(True)

# Save the figure
plt.savefig("MaxTempInWorldCities.png")

# Show plot
plt.show()
```


![png](output_9_0.png)



```python
# Build a scatter plot for each data type 
#Humidity vs. Latitude

plt.scatter(lat_data, humidity_data, marker="o")

# Incorporate the other graph properties
plt.title("Latitude in World Cities vs. Humidity")
plt.ylabel("Humidity")
plt.xlabel("Latitude")
plt.grid(True)

# Save the figure
plt.savefig("HumidityInWorldCities.png")

# Show plot
plt.show()
```


![png](output_10_0.png)



```python
# Build a scatter plot for each data type 
#Cloudiness (%) vs. Latitude

plt.scatter(lat_data, cloudiness_data, marker="o")

# Incorporate the other graph properties
plt.title("Latitude in World Cities vs. Cloudiness")
plt.ylabel("Cloudiness")
plt.xlabel("Latitude")
plt.grid(True)

# Save the figure
plt.savefig("CloudinessInWorldCities.png")

# Show plot
plt.show()
```


![png](output_11_0.png)



```python
# Build a scatter plot for each data type 
#Wind Speed (mph) vs. Latitude

plt.scatter(lat_data, windspeed_data, marker="o")

# Incorporate the other graph properties
plt.title("Latitude in World Cities vs. Wind Speed")
plt.ylabel("Wind Speed")
plt.xlabel("Latitude")
plt.grid(True)

# Save the figure
plt.savefig("WindSpeedInWorldCities.png")

# Show plot
plt.show()
```


![png](output_12_0.png)



```python

```
