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

<!-- Элементы выровнены по центру основной оси -->
#pond {
  display: flex;
  justify-content: center;
}

<!-- Равномерные отступы вокруг элементов; между элементами вдвое больше пространства, чем от краёв -->
#pond {
  display: flex;
  justify-content: space-around;
}

<!-- Равномерное распределение свободного пространства между элементами; первый и последний элементы прижаты к краям -->
#pond {
  display: flex;
  justify-content: space-between;
}

<!-- 
  ALIGN-ITEMS: Выравнивание по поперечной оси (вертикальной по умолчанию)
-->

<!-- Элементы выравниваются по нижнему краю контейнера -->
#pond {
  display: flex;
  align-items: flex-end;
}

<!-- Комбинация: центрирование по обеим осям -->
#pond {
  display: flex;
  justify-content: center;
  align-items: center;
}

<!-- Комбинация: space-around по основной оси и flex-end по поперечной -->
#pond {
  display: flex;
  justify-content: space-around;
  align-items: flex-end;
}

<!-- 
  FLEX-DIRECTION: Направление основной оси
-->

<!-- Элементы отображаются в обратном порядке к направлению текста -->
#pond {
  display: flex;
  flex-direction: row-reverse;
}

<!-- Элементы располагаются сверху вниз -->
#pond {
  display: flex;
  flex-direction: column;
}

<!-- Комбинация: row-reverse с выравниванием по левому краю -->
#pond {
  display: flex;
  flex-direction: row-reverse;
  justify-content: left;
}

<!-- Комбинация: column с выравниванием по концу основной оси -->
#pond {
  display: flex;
  flex-direction: column;
  justify-content: end;
}

<!-- Комбинация: column-reverse с равномерным распределением пространства -->
#pond {
  display: flex;
  flex-direction: column-reverse;
  justify-content: space-between;
}

<!-- Комбинация: row-reverse с центрированием и выравниванием по концу поперечной оси -->
#pond {
  display: flex;
  flex-direction: row-reverse;
  justify-content: center;
  align-items: end;
}

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

#pond {
  display: flex;
}
.red {
  order: -3;
}

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

<!-- Комбинация order и align-self для одного элемента -->
#pond {
  display: flex;
  align-items: flex-start;
}
.yellow {
  order: 2;
  align-self: end;
}

<!-- 
  FLEX-WRAP: Перенос элементов на новую строку
  По умолчанию flex-wrap: nowrap (все элементы в одну строку)
-->

<!-- Элементы автоматически переносятся на новую строку -->
#pond {
  display: flex;
  flex-wrap: wrap;
}

<!-- Комбинация column direction с wrap -->
#pond {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
}

<!-- 
  FLEX-FLOW: Сокращённая запись для flex-direction и flex-wrap
  Принимает два значения через пробел: направление и перенос
-->

#pond {
  display: flex;
  flex-flow: column wrap;
}

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

#pond {
  display: flex;
  flex-wrap: wrap;
  align-content: flex-end;
}

<!-- Комбинация column-reverse с центрированием содержимого -->
#pond {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column-reverse;
  align-content: center;
}

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

<!-- 
  Поздравляем! Вы освоили CSS Flexbox!
  Ты выиграл! Благодарим тебя за мастерство flexbox, 
  ты смог помочь всем лягушатам добраться до своих лилий. 
  Просто взгляни, как они счастливы!
-->
```
