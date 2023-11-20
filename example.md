## Комп'ютерні системи імітаційного моделювання
## СПм-22-4, **Уваров Георгій Олексійович**
### Лабораторна робота №**2**. Редагування імітаційних моделей у середовищі NetLogo

<br>

### Варіант 7, модель у середовищі NetLogo:
Wolf Sheep Predation. Прибрати "зграйність" вовків - тепер перед початком свого ходу вовки повинні "оглядатися", перевіряючи оточення, та обирати напрямок руху виходячи з наявності вівець та відсутності інших вовків. Якщо немає іншої можливості – переміщається випадково. При знаходженні на одній ділянці поля двох вовків залишається лише один з них. Вівці переміщаються випадковим чином, але при виявленні вовка на одній із клітин поруч змінюють напрямок на протилежний.

<br>

### Внесені зміни у вихідну логіку моделі, за варіантом:

**Вівці обходять вовків**

<pre>
to avoid-wolves   ; wolf procedure
  ifelse sum [count wolves-here] of neighbors = 0 [
    move;
  ]
  [
    repeat 4 [
      if (any? wolves in-cone 1.2 90 ) [
        rt 90;
      ]
    ]
    fd 1;
  ]
end
</pre>

**Вовки обходять вовків та шукають овець**

<pre>
to seek-sheep   ;   wolf procedure
  ifelse sum [count sheep-here] of neighbors = 0 [
    if not (any? sheep-here)[
      set color black;
      move; move randomly
    ]
  ]
  [
    set color red;
    repeat 6 [
      if not (any? sheep in-cone 2 60 ) [
        rt 60;
      ]
      if (any? wolves in-cone 2 60 ) [
        rt 60;
      ]
    ]
    fd 1;
  ]
end
</pre>

### Внесені зміни у вихідну логіку моделі, на власний розсуд:

**Вовки, що рухаються цілеспрямовано, красяться у червоний**.

<pre>
to seek-sheep   ;   wolf procedure
  ifelse sum [count sheep-here] of neighbors = 0 [
    if not (any? sheep-here)[
      set color black;
      move; move randomly
    ]
  ]
  [
    set color red;
    repeat 6 [
      if not (any? sheep in-cone 2 60 ) [
        rt 60;
      ]
      if (any? wolves in-cone 2 60 ) [
        rt 60;
      ]
    ]
    fd 1;
  ]
end
</pre>

## Обчислювальні експерименти
*// тут повинен бути наведений опис одного експерименту, за аналогією з першої л/р.* 
### 1. Вплив дисциплінованості водіів на середню швидкість переміщення
