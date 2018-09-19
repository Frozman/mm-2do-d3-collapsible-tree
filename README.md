# mm-2do-d3-collapsible-tree
Скрипт на базе примера d3.js Collapsible Tree 
https://bl.ocks.org/mbostock/4339083

Цель:
создать программу, которая позволяет объединить три уровня организации дел в одном простом скрипте:
список дел       - task manager
карта идей       - mind map
поток ценности   - finance management

1 часть: ВИЗУАЛИЗИАЦИЯ "ручного" JSON

# исходный flare.json

{
     "name": "cluster",
     "children": [
      {"name": "AgglomerativeCluster", "size": 3938},
      {"name": "CommunityStructure", "size": 3812},
      {"name": "HierarchicalCluster", "size": 6714},
      {"name": "MergeEdge", "size": 743}
     ]
    }

# новый flare.v1.json

            {
              "name": "level4",
              "link": "https://www.mindmaps.app/",
              "image": "file.png",
              "notes": "заметка",
              "color": "red",
             
              "size": 3938
            },


ЦЕННОСТЬ:

size оставим из оригинального файла - этот показатель будет нам говорить о ценности задачи, выражаясь в деньгах или времени

sum-size = сумма size для children



ЗАДАЧИ:

"name": "level4",
"link": "https://www.mindmaps.app/",
"image": "file.png"  
"notes": "текстовая заметка"
"color": "red",



СТРУКТУРА:

id
parrent-id


или вложенность "children": []



список задач от простого к сложному:


1) 
sum-size = сумма size children 
вычислить 

stroke-width = sum-size * норм
в d3 это  diagonal 

2)
также sum-size влияет на размер родительского circle, то есть родительские circle всегда больше и включают детей 

circle -> r = {"size":x}


3) 
в родительских circle "упаковать" количество детей – в виде встроенной окружности размером rmnin

4) ввести sum-color 

шкалу от красного через желтый до зеленого

забирать из JSON значение для ноды: красный, желтый, зеленый и вычислять sum-color, 
который использовать для подсветки родительских кругов и диагоналей

sum-color=size*green+size*yell ow+size*red


ПРИМЕРЫ

1 https://tobloef.com/text2mindmap/ редактировать в колонке справа JSON как бы вручную

2 http://mofas.github.io/mindMap/dist/index.html редактирование/удаление

3 https://adeelk93.github.io/collapsibleTree/ еще примеры по размеру и цвету

4 https://www.mindmaps.app/
