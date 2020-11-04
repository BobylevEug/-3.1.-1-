## ___Домашнее задание к занятию "3.1. Работа в терминале, лекция 1"___

#5.
  - RAM 1Gb
  - Видеопамять 8Mb
  - Порт сервера удаленного устройства
  
#6.
  - RAM 2Gb
    v.customize ["modifyvm", :id, "--memory", [ENV['DISCOURSE_VM_MEM'].to_i, 2048].max]
  
  - Под Win (2 ядра процессора)
    cpu_count = 2

  - Под Linux или Mac (все ядра)
    if RUBY_PLATFORM =~ /linux/
    cpu_count = `nproc`.to_i
    elsif RUBY_PLATFORM =~ /darwin/
    cpu_count = `sysctl -n hw.ncpu`.to_i
    end

  - Гостевая ось
    v.customize ["modifyvm", :id, "--cpus", cpu_count]

Vagrant reload

#8.

  - export HISTSIZE=1000 1000 команд
  line702
  
  - export HISTFILESIZE=1000 1000 строк
  line698
  
  - export HISTCONTROL=ignorespace:erasedups
  - ignorespace	`не сохранять строки начинающиеся с символа <пробел>`
  - ignoredups	`не сохранять строки, совпадающие с последней выполненной командой`
  - ignoreboth	использовать обе опции ‘ignorespace’ и ‘ignoredups’
  
#9.

  - () и {} применимы для объединения нескольких команд в один оставной оператор
  - () - выполняется в отдельном подпроцессе, работает на 18,5% медленнее
  - {} - выполняется в контексте текущей оболочки, на 56,2% меньше задействования процессорного времени
  - line 473
  
#10.

- touch testfile{1..100000} создает 100000 пустых файлов testfile1, testfile2 в данной директории
- touch testfile{1..300000} Выдает ошибку : Argument list too long

- rm testfile{1..100000} удаление 10000 файлов

#11.

- sudo cp /bin/bash /tmp/new_path_directory/bash копирование Bash
- export PATH=/tmp/new_path_directory:/usr/local/bin/bash:/bin/bash:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin задание путей поиска в переменной PATH
- type -a bash вывод нахождения bash в разных директориях

#12.

- at выполняет задачи в поставленное время
- batch  выполняет задачи во время низкой загруженности системы 
