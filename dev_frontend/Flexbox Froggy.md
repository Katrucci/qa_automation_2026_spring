
### CSS Flexbox: Полное руководство на примере игры с лягушками

<!-- 
  Это интерактивное руководство по CSS Flexbox.
  Каждый пример показывает, как различные свойства flexbox влияют на расположение элементов.
  Визуализация происходит на примере пруда с лягушками и кувшинками.
-->

<!-- 
  JUSTIFY-CONTENT: Выравнивание по основной оси (горизонтальной по умолчанию)
-->

<!-- Элементы прижаты к концу основной оси --><br>
#### pond {
  display: flex;<br>
  justify-content: flex-end;<br>
}

<table>
  <tr>
    <td><img src="images/froggy1_1.png" alt="Froggy_1_1" width="400"/></td>
    <td><img src="images/froggy1_2.png" alt="Froggy_1_2" width="400"/></td>
  </tr>
</table>

<!-- Элементы выровнены по центру основной оси --><br>
#### pond {
  display: flex;<br>
  justify-content: center;<br>
}

<table>
  <tr>
    <td><img src="images/froggy2_1.png" alt="Froggy_2_1" width="400"/></td>
    <td><img src="images/froggy2_2.png" alt="Froggy_2_2" width="400"/></td>
  </tr>
</table>

<!-- Равномерные отступы вокруг элементов; между элементами вдвое больше пространства, чем от краёв --><br>
#### pond {
  display: flex;<br>
  justify-content: space-around;<br>
}

<table>
  <tr>
    <td><img src="images/froggy3_1.png" alt="Froggy_3_1" width="400"/></td>
    <td><img src="images/froggy3_2.png" alt="Froggy_3_2" width="400"/></td>
  </tr>
</table>
<!-- Равномерное распределение свободного пространства между элементами; первый и последний элементы прижаты к краям --><br>

#### pond  {
  display: flex;<br>
  justify-content: space-between;<br>
}

<table>
  <tr>
    <td><img src="images/froggy4_1.png" alt="Froggy_4_1" width="400"/></td>
    <td><img src="images/froggy4_2.png" alt="Froggy_4_2" width="400"/></td>
  </tr>
</table>
<!-- 
  ALIGN-ITEMS: Выравнивание по поперечной оси (вертикальной по умолчанию)
-->

<!-- Элементы выравниваются по нижнему краю контейнера --><br>
#### pond {
  display: flex;<br>
  align-items: flex-end;<br>
}


<table>
  <tr>
    <td><img src="images/froggy5_1.png" alt="Froggy_5_1" width="400"/></td>
    <td><img src="images/froggy5_2.png" alt="Froggy_5_2" width="400"/></td>
  </tr>
</table>
<!-- Комбинация: центрирование по обеим осям --><br>

#### pond {
  display: flex;<br>
  justify-content: center;<br>
  align-items: center;<br>
}

<table>
  <tr>
    <td><img src="images/froggy6_1.png" alt="Froggy_6_1" width="400"/></td>
    <td><img src="images/froggy6_2.png" alt="Froggy_6_2" width="400"/></td>
  </tr>
</table>
<!-- Комбинация: space-around по основной оси и flex-end по поперечной --><br>

#### pond  {
  display: flex;<br>
  justify-content: space-around;<br>
  align-items: flex-end;<br>
}

<table>
  <tr>
    <td><img src="images/froggy7_1.png" alt="Froggy_7_1" width="400"/></td>
    <td><img src="images/froggy7_2.png" alt="Froggy_7_2" width="400"/></td>
  </tr>
</table>
<!-- 
  FLEX-DIRECTION: Направление основной оси
-->

<!-- Элементы отображаются в обратном порядке к направлению текста --><br>
#### pond {
  display: flex;<br>
  flex-direction: row-reverse;<br>
}

<table>
  <tr>
    <td><img src="images/froggy8_1.png" alt="Froggy_8_1" width="400"/></td>
    <td><img src="images/froggy8_2.png" alt="Froggy_8_2" width="400"/></td>
  </tr>
</table>
<!-- Элементы располагаются сверху вниз --><br>

#### pond{
  display: flex;<br>
  flex-direction: column;<br>
}

<table>
  <tr>
    <td><img src="images/froggy9_1.png" alt="Froggy_9_1" width="400"/></td>
    <td><img src="images/froggy9_2.png" alt="Froggy_9_2" width="400"/></td>
  </tr>
</table>
<!-- Комбинация: row-reverse с выравниванием по левому краю --><br>

#### pond {
  display: flex;
  flex-direction: row-reverse;<br>
  justify-content: left;<br>
}

<table>
  <tr>
    <td><img src="images/froggy10_1.png" alt="Froggy_10_1" width="400"/></td>
    <td><img src="images/froggy10_2.png" alt="Froggy_10_2" width="400"/></td>
  </tr>
</table>
<!-- Комбинация: column с выравниванием по концу основной оси --><br>

#### pond {
  display: flex;<br>
  flex-direction: column;<br>
  justify-content: end;<br>
}

<table>
  <tr>
    <td><img src="images/froggy11_1.png" alt="Froggy_11_1" width="400"/></td>
    <td><img src="images/froggy11_2.png" alt="Froggy_11_2" width="400"/></td>
  </tr>
</table>
<!-- Комбинация: column-reverse с равномерным распределением пространства --><br>

#### pond {
  display: flex;<br>
  flex-direction: column-reverse;<br>
  justify-content: space-between;<br>
}

<table>
  <tr>
    <td><img src="images/froggy12_1.png" alt="Froggy_12_1" width="400"/></td>
    <td><img src="images/froggy12_2.png" alt="Froggy_12_2" width="400"/></td>
  </tr>
</table>
<!-- Комбинация: row-reverse с центрированием и выравниванием по концу поперечной оси --><br>

#### pond {
  display: flex;<br>
  flex-direction: row-reverse;<br>
  justify-content: center;<br>
  align-items: end;<br>
}

<table>
  <tr>
    <td><img src="images/froggy13_1.png" alt="Froggy_13_1" width="400"/></td>
    <td><img src="images/froggy13_2.png" alt="Froggy_13_2" width="400"/></td>
  </tr>
</table>
<!-- 
  ORDER: Изменение порядка отдельных элементов
  По умолчанию все элементы имеют order: 0
  Элементы с меньшим значением order располагаются раньше
--><br>

#### pond {
  display: flex;<br>
}<br>
.yellow {<br>
  order: 2;<br>
}

<table>
  <tr>
    <td><img src="images/froggy14_1.png" alt="Froggy_14_1" width="400"/></td>
    <td><img src="images/froggy14_2.png" alt="Froggy_14_2" width="400"/></td>
  </tr>
</table><br>

#### pond {
  display: flex;<br>
}<br>
.red {<br>
  order: -3;<br>
}

<table>
  <tr>
    <td><img src="images/froggy15_1.png" alt="Froggy_15_1" width="400"/></td>
    <td><img src="images/froggy15_2.png" alt="Froggy_15_2" width="400"/></td>
  </tr>
</table>
<!-- 
  ALIGN-SELF: Индивидуальное выравнивание отдельных элементов
  Переопределяет align-items для конкретного элемента
--><br>

#### pond {
  display: flex;<br>
  align-items: flex-start;<br>
}<br>
.yellow {<br>
  align-self: end;<br>
}

<table>
  <tr>
    <td><img src="images/froggy16_1.png" alt="Froggy_16_1" width="400"/></td>
    <td><img src="images/froggy16_2.png" alt="Froggy_16_2" width="400"/></td>
  </tr>
</table>
<!-- Комбинация order и align-self для одного элемента --><br>

#### pond {
  display: flex;<br>
  align-items: flex-start;<br>
}<br>
.yellow {<br>
  order: 2;<br>
  align-self: end;<br>
}

<table>
  <tr>
    <td><img src="images/froggy17_1.png" alt="Froggy_17_1" width="400"/></td>
    <td><img src="images/froggy17_2.png" alt="Froggy_17_2" width="400"/></td>
  </tr>
</table>
<!-- 
  FLEX-WRAP: Перенос элементов на новую строку
  По умолчанию flex-wrap: nowrap (все элементы в одну строку)
-->

<!-- Элементы автоматически переносятся на новую строку --><br>

#### pond {
  display: flex;<br>
  flex-wrap: wrap;<br>
}

<table>
  <tr>
    <td><img src="images/froggy18_1.png" alt="Froggy_18_1" width="400"/></td>
    <td><img src="images/froggy18_2.png" alt="Froggy_18_2" width="400"/></td>
  </tr>
</table>
<!-- Комбинация column direction с wrap --><br>

#### pond {
  display: flex;<br>
  flex-direction: column;<br>
  flex-wrap: wrap;<br>
}
<table>
  <tr>
    <td><img src="images/froggy19_1.png" alt="Froggy_19_1" width="400"/></td>
    <td><img src="images/froggy19_2.png" alt="Froggy_19_2" width="400"/></td>
  </tr>
</table>
<!-- 
  FLEX-FLOW: Сокращённая запись для flex-direction и flex-wrap
  Принимает два значения через пробел: направление и перенос
  
--><br>
#### pond {
  display: flex;<br>
  flex-flow: column wrap;<br>
}

<table>
  <tr>
    <td><img src="images/froggy20_1.png" alt="Froggy_20_1" width="400"/></td>
    <td><img src="images/froggy20_2.png" alt="Froggy_20_2" width="400"/></td>
  </tr>
</table>
<!-- 
  ALIGN-CONTENT: Управление пространством между рядами (только при flex-wrap: wrap)
  Важно: align-content работает только когда элементов больше, чем помещается в одном ряду
  Когда только один ряд, align-content ни на что не влияет
  Это может запутать, но align-content отвечает за расстояние между рядами, 
  в то время как align-items отвечает за то, как элементы в целом будут выровнены в контейнере
--><br>

#### pond {
  display: flex;<br>
  flex-wrap: wrap;<br>
  align-content: flex-start;<br>
}

<table>
  <tr>
    <td><img src="images/froggy21_1.png" alt="Froggy_21_1" width="400"/></td>
    <td><img src="images/froggy21_2.png" alt="Froggy_21_2" width="400"/></td>
  </tr>
</table><br>

#### pond {
  display: flex;<br>
  flex-wrap: wrap;<br>
  align-content: flex-end;<br>
}

<table>
  <tr>
    <td><img src="images/froggy22_1.png" alt="Froggy_22_1" width="400"/></td>
    <td><img src="images/froggy22_2.png" alt="Froggy_22_2" width="400"/></td>
  </tr>
</table>
<!-- Комбинация column-reverse с центрированием содержимого --><br>

#### pond {
  display: flex;<br>
  flex-wrap: wrap;<br>
  flex-direction: column-reverse;<br>
  align-content: center;<br>
}

<table>
  <tr>
    <td><img src="images/froggy23_1.png" alt="Froggy_23_1" width="400"/></td>
    <td><img src="images/froggy23_2.png" alt="Froggy_23_2" width="400"/></td>
  </tr>
</table>
<!-- 
  ФИНАЛЬНАЯ КОМБИНАЦИЯ: Все свойства вместе
  Сложный пример использования множества flexbox свойств
--><br>

#### pond  {
  display: flex;<br>
  flex-flow: wrap-reverse;<br>
  align-content: space-between;<br>
  justify-content: center;<br>
  flex-direction: column-reverse;<br>
}
<table>
  <tr>
    <td><img src="images/froggy24_1.png" alt="Froggy_24_1" width="400"/></td>
    <td><img src="images/froggy24_2.png" alt="Froggy_24_2" width="400"/></td>
  </tr>
</table><br>

  **Поздравляем! Вы освоили CSS Flexbox!**<br>
  Ты выиграл! Благодарим тебя за мастерство flexbox, <br>
  ты смог помочь всем лягушатам добраться до своих лилий.<br> 
  **Просто взгляни, как они счастливы!**<br>
![Froggy_final](images/froggy_final.png)
