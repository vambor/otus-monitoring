# Домашнее задание Настройка алертинга (Zabbix)

## Описание
На виртуальной машине установлен Zabbix Server 7.4.5 и прочие его компоненты для мониторинга метрик
Реализована автоматическая отправка уведомлений в TG при превышении порогового значения в 95

```
#!/bin/bash
# /usr/local/bin/otus_metrics.sh

if [ "$#" -eq 0 ]; then
  cat <<EOF
{"data":[
  {"{#METRIC}":"metric1"},
  {"{#METRIC}":"metric2"},
  {"{#METRIC}":"metric3"}
]}
EOF
else
  METRIC="$1"
  case "$METRIC" in
    metric1|metric2|metric3)
      echo $((RANDOM%101))
      ;;
    *)
      echo 0
      ;;
  esac
fi
```
При вызове без аргументов возвращается JSON в формате LDD:
```
{"data":[{"{#METRIC}":"metric1"},{"{#METRIC}":"metric2"},{"{#METRIC}":"metric3"}]}
```
При вызове с параметром (metric1 || 2 || 3) возвращает случайное число от 0 до 100

За Discovery Rule отвечает ключ otus.lld (вызов без аргументов)
За Item prototype отвечает ключ otus.value[{#METRIC}] типа Numeric (unsigned)
Trigger prototype срабатывает при last() >= 95
