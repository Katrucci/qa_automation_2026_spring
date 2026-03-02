```markdown
# CSS Flexbox: Полное руководство на примере игры с лягушками

<!-- 
  Это интерактивное руководство по CSS Flexbox.
  Каждый пример показывает, как различные свойства flexbox влияют на расположение элементов.
  Визуализация происходит на примере пруда с лягушками и кувшинками.
-->

<!-- 
  JUSTIFY-CONTENT: Выравнивание по основной оси (горизонтальной по умолчанию)
-->

<!-- Элементы прижаты к концу основной оси -->
#pond {
  display: flex;
  justify-content: flex-end;
}
![Froggy_1_1](https://raw.githubusercontent.com/Katrucci/qa_automation_2026_spring/main/dev_frontend/images/froggy1_1.png)
![Froggy_1_2](./images/froggy1_2.png)


<!-- Элементы выровнены по центру основной оси -->
#pond {
  display: flex;
  justify-content: center;
}
![Froggy_2_1](images/froggy2_1.png)
![Froggy_2_2](images/froggy2_2.png)

<!-- Равномерные отступы вокруг элементов; между элементами вдвое больше пространства, чем от краёв -->
#pond {
  display: flex;
  justify-content: space-around;
}
![Froggy_3_1](images/froggy3_1.png)
![Froggy_3_2](images/froggy3_2.png)

<!-- Равномерное распределение свободного пространства между элементами; первый и последний элементы прижаты к краям -->
#pond {
  display: flex;
  justify-content: space-between;
}
![Froggy_4_1](images/froggy4_1.png)
![Froggy_4_2](images/froggy4_2.png)
<!-- 
  ALIGN-ITEMS: Выравнивание по поперечной оси (вертикальной по умолчанию)
-->

<!-- Элементы выравниваются по нижнему краю контейнера -->
#pond {
  display: flex;
  align-items: flex-end;
}
![Froggy_5_1](images/froggy5_1.png)
![Froggy_5_2](images/froggy5_2.png)
<!-- Комбинация: центрирование по обеим осям -->
#pond {
  display: flex;
  justify-content: center;
  align-items: center;
}
![Froggy_6_1](images/froggy6_1.png)
![Froggy_6_2](images/froggy6_2.png)
<!-- Комбинация: space-around по основной оси и flex-end по поперечной -->
#pond {
  display: flex;
  justify-content: space-around;
  align-items: flex-end;
}
![Froggy_7_1](images/froggy7_1.png)
![Froggy_7_2](images/froggy7_2.png)
<!-- 
  FLEX-DIRECTION: Направление основной оси
-->

<!-- Элементы отображаются в обратном порядке к направлению текста -->
#pond {
  display: flex;
  flex-direction: row-reverse;
}
![Froggy_8_1](images/froggy8_1.png)
![Froggy_8_2](images/froggy8_2.png)
<!-- Элементы располагаются сверху вниз -->
#pond {
  display: flex;
  flex-direction: column;
}
![Froggy_9_1](images/froggy9_1.png)
![Froggy_9_2](images/froggy9_2.png)
<!-- Комбинация: row-reverse с выравниванием по левому краю -->
#pond {
  display: flex;
  flex-direction: row-reverse;
  justify-content: left;
}
![Froggy_10_1](images/froggy10_1.png)
![Froggy_10_2](images/froggy10_2.png)
<!-- Комбинация: column с выравниванием по концу основной оси -->
#pond {
  display: flex;
  flex-direction: column;
  justify-content: end;
}
![Froggy_11_1](images/froggy11_1.png)
![Froggy_11_2](images/froggy11_2.png)
<!-- Комбинация: column-reverse с равномерным распределением пространства -->
#pond {
  display: flex;
  flex-direction: column-reverse;
  justify-content: space-between;
}
![Froggy_12_1](images/froggy12_1.png)
![Froggy_12_2](images/froggy12_2.png)
<!-- Комбинация: row-reverse с центрированием и выравниванием по концу поперечной оси -->
#pond {
  display: flex;
  flex-direction: row-reverse;
  justify-content: center;
  align-items: end;
}
![Froggy_13_1](images/froggy13_1.png)
![Froggy_13_2](images/froggy13_2.png)
<!-- 
  ORDER: Изменение порядка отдельных элементов
  По умолчанию все элементы имеют order: 0
  Элементы с меньшим значением order располагаются раньше
-->

#pond {
  display: flex;
}
.yellow {
  order: 2;
}
![Froggy_14_1](images/froggy14_1.png)
![Froggy_14_2](images/froggy14_2.png)

#pond {
  display: flex;
}
.red {
  order: -3;
}
![Froggy_15_1](images/froggy15_1.png)
![Froggy_15_2](images/froggy15_2.png)
<!-- 
  ALIGN-SELF: Индивидуальное выравнивание отдельных элементов
  Переопределяет align-items для конкретного элемента
-->

#pond {
  display: flex;
  align-items: flex-start;
}
.yellow {
  align-self: end;
}
![Froggy_16_1](images/froggy16_1.png)
![Froggy_16_2](images/froggy16_2.png)
<!-- Комбинация order и align-self для одного элемента -->
#pond {
  display: flex;
  align-items: flex-start;
}
.yellow {
  order: 2;
  align-self: end;
}
![Froggy_17_1](images/froggy17_1.png)
![Froggy_17_2](images/froggy17_2.png)
<!-- 
  FLEX-WRAP: Перенос элементов на новую строку
  По умолчанию flex-wrap: nowrap (все элементы в одну строку)
-->

<!-- Элементы автоматически переносятся на новую строку -->
#pond {
  display: flex;
  flex-wrap: wrap;
}
![Froggy_18_1](images/froggy18_1.png)
![Froggy_18_2](images/froggy18_2.png)
<!-- Комбинация column direction с wrap -->
#pond {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
}
![Froggy_19_1](images/froggy19_1.png)
![Froggy_19_2](images/froggy19_2.png)
<!-- 
  FLEX-FLOW: Сокращённая запись для flex-direction и flex-wrap
  Принимает два значения через пробел: направление и перенос
-->

#pond {
  display: flex;
  flex-flow: column wrap;
}
![Froggy_20_1](images/froggy20_1.png)
![Froggy_20_2](images/froggy20_2.png)
<!-- 
  ALIGN-CONTENT: Управление пространством между рядами (только при flex-wrap: wrap)
  Важно: align-content работает только когда элементов больше, чем помещается в одном ряду
  Когда только один ряд, align-content ни на что не влияет
  Это может запутать, но align-content отвечает за расстояние между рядами, 
  в то время как align-items отвечает за то, как элементы в целом будут выровнены в контейнере
-->

#pond {
  display: flex;
  flex-wrap: wrap;
  align-content: flex-start;
}
![Froggy_21_1](images/froggy21_1.png)
![Froggy_21_2](images/froggy21_2.png)
#pond {
  display: flex;
  flex-wrap: wrap;
  align-content: flex-end;
}
![Froggy_22_1](images/froggy22_1.png)
![Froggy_22_2](images/froggy22_2.png)
<!-- Комбинация column-reverse с центрированием содержимого -->
#pond {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column-reverse;
  align-content: center;
}
![Froggy_23_1](images/froggy23_1.png)
![Froggy_23_2](images/froggy23_2.png)
<!-- 
  ФИНАЛЬНАЯ КОМБИНАЦИЯ: Все свойства вместе
  Сложный пример использования множества flexbox свойств
-->
#pond {
  display: flex;
  flex-flow: wrap-reverse;
  align-content: space-between;
  justify-content: center;
  flex-direction: column-reverse;
}
![Froggy_24_1](images/froggy24_1.png)
![Froggy_24_2](images/froggy24_2.png)
<!-- 
  Поздравляем! Вы освоили CSS Flexbox!
  Ты выиграл! Благодарим тебя за мастерство flexbox, 
  ты смог помочь всем лягушатам добраться до своих лилий. 
  Просто взгляни, как они счастливы!
-->
![Froggy_final](images/froggy_final.png)
```
