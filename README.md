# "Hello world!" in perl
[История Perl](https://habr.com/ru/post/305402/)
***
    #!/usr/bin/perl
    $_=q$qsjou<vd<r<aia+<rr<bfmmp+<xpsme=\ob$;
    y?<-@*-.b-z? -$+-/a-y?;s=\D+=$&=ee

### Будьте [осторожны](http://lurkmore.to/Программа_из_одной_строчки_на_Perl) с запуском [обфусцированного кода](https://ru.wikipedia.org/wiki/Обфускация_(программное_обеспечение)) на своём компьютере!

Этот код можно назвать примером обфускации.  
Еще в нём можно увидеть некоторые особенности Perl:

+ Cпециальные переменные (позволяют получать различные параметры запуска скрипта, название ОС, время запуска, код последней ошибки и др.)  
+ Неявная передача параметров внутри программы с помощью специальных переменных.  
+ Гибкий синтаксис.
+ Поддержка регулярных выражений.  

#### Как это работает:

##### Кавычки.
Двойные и одинарные кавычки в Perl различаются по поведению.  
Операторы q и qq обозначают одинарные и двойные кавычки.  
Вместо скобок можно использовать любые символы: 

    qq(), qq{}, q<>, q[], q//, q**, q@@, q44 и т.д.
    
что позволяет использовать символы внутри строки без экранирования.
    
    

##### Точка с запятой.
Служит для разделеия операторов. В конце файла не обязательна.  

##### Специальная переменная $_ .
По умолчанию хранит аргументы переданные программе, и во время исполнения, результаты поиска по заданному образцу, присваивание, и др.  

    $_=q$qsjou<vd<r<aia+<rr<bfmmp+<xpsme=\ob$;
           |
           V
    $_="qsjou<vd<r<aia+<rr<bfmmp+<xpsme=\ob";

##### Регулярные выражения.
"Основной особенностью языка считаются его богатые возможности для работы с текстом, в том числе работа с регулярными выражениями" - [wiki](https://ru.wikipedia.org/wiki/Perl)  
В примере для работы с текстом применяются два оператора: y и s.  

**y** - оператор замены множества символов или транслитерации(ещё одно имя оперетора - tr)  
**s** - поиск и замена подстроки.  

    y/SEARCHLIST/REPLACEMENTLIST/flags
    
Флаги не обязательны.  
В качестве разделителей, вместо "/" могут использоваться любые символы.  
В примере "?" и "=" - разделители, а списки SEARCHLIST и REPLACEMENTLIST заданы с помощью регулярных выражений, диапазонами символов:

    "<-@*-.b-z" - диапазоны [от "<" до "@" включительно] ["*" - "."] ["b" - "z"]
    будут заменены на
    " -$+-/a-y" - ["пробел" - "$"] ["+" - "/"] ["a" - "y"]
 
После выполнения оператора  

    y?<-@*-.b-z? -$+-/a-y?;

значением переменной $_ будет  

    print uc q aha, qq aello, world!\na

если заменить оператор q на кавычки, то переменная $_ будет выглядеть так:

    print uc 'h', "ello, world!\n"

"s" по умолчанию работает с переменной $_ , 
    флаг "ee" в операторе  - [eval](https://perldoc.perl.org/perlop.html#s%2f_PATTERN_%2f_REPLACEMENT_%2fmsixpodualngcer)
приведет к вычислению выражения

    print uc 'h', "ello, world!\n"
    
print по умолчанию печатает в STDOUT, uc - "uppercase"
