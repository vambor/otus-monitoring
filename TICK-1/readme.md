# Домашнее задание Установка и настройка TICK стека

## Описание
На виртуальной машине c CMS Wordpress, nginx, php8.4-fpm, MariaDB были установлены компоненты chronograf, telegraf, influx 1.12, kapacitor.

Kapacitor настроен на чтение статисткики\метрик из машины-хоста, nginx, phpfpm, mysql. Получаемая информация настроена на передачу в influxdb.

Произведена настройка Chronograf с influxdb и kapacitor.

Созданы дашборды метрик dashboards.png

Созданы алёрты по CPU и доступу к php-fpm alerts.png
