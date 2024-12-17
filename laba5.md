Лабораторная работа 5
===========================
*Выполнил Кармазин А.З. 466125, K3161*

#### 1. Создание bash-скрипта

Код проверяет расширение файлов подготовленных к коммиту а также наличие в них крайне важной строки "Hakuna Matata"

```
#!/bin/bash

files_to_commit=$(git diff --cached --name-only)
error_code=0

for file in $files_to_commit; do
	if [[ "$file" != *.txt ]]; then
    	echo "Whoops... It seems that '$file' is not .txt."
    	error_code=1
		break
	fi
	if [[ $(grep -i -c "hakuna matata" "$file") -eq 0 ]]; then
    	echo "Bad news... '$file' does not have 'Hakuna Matata' string"
    	error_code=2
    	break
	fi
done


if [ "$error_code" != 0 ]; then
	echo "Commit denied"
	exit 1
fi

if [ "$error_code" = 0 ]; then
	echo "You are committing .txt file(s) and they have 'Hakuna Matata' string"
	exit 0
fi
```
<image src=example01.PNG>
<image src=example2.PNG>
<image src=example3.PNG>

#### 2. Работа с GitFlow

1. GitFlow по умолчанию установлен на моей машине
2. В корне репозитория я инициализировал GitFlow и добавил ветку для добавления новых фич. Создал файл task_manager.py и внес изменения.

<image src=step1.PNG>

3. Завершил работу с веткой для добавления новой функциональности

<image src=step2.PNG>

4. Добавил новый релиз в соответствующей ветке

<image src=step4.PNG>

5. Завершил работу с веткой релизов

<image src=step5.PNG>

6. "Обнаружил" критическую ошибку. Начал ветку hotfix по оперативному устранению неполадок

<image src=step6.PNG>
<image src=step7.PNG>

7. Ошибки устранены. Изменения отправлены на удаленный репозиторий
