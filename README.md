# Настройки BB для нового офиса

Всё, что нужно, чтобы BB у нового человека выглядел и работал как надо: темы и список
плагинов. Ставится копипастом, вручную ничего не скачивается.

## Установка целиком

```bash
git clone https://github.com/leonovs0808-star/bb-nastroyki.git /tmp/bb-nastroyki
cp -r /tmp/bb-nastroyki/themes/* "$(bb theme dir)/"
bb theme set g1-mustard-dark

bb plugin install git:https://github.com/leonovs0808-star/bb-plugin-office-files.git
bb plugin install git:https://github.com/leonovs0808-star/bb-plugin-markdown-view.git
bb plugin install git:https://github.com/leonovs0808-star/bb-plugin-notify.git
bb plugin install git:https://github.com/vburojevic/bb-plugin-ayu
bb plugin install git:https://github.com/vburojevic/bb-plugin-pets
bb plugin install git:https://github.com/gtramontina/bb-plugin-chime

bb theme show && bb plugin list
```

## Темы

| Имя | Что это |
|---|---|
| `g1-mustard-dark` | тёмная, горчичный акцент — основная |
| `ayu-mirage-crisp-icons` | тёмная, вариант ayu с чёткими иконками |

Тема — это папка с файлом `theme.css`. Команды установки у неё нет: папка кладётся в
`bb theme dir`, дальше `bb theme set <имя>`. Путь у каждого свой, поэтому в командах выше он
подставляется сам через `$(bb theme dir)`.

## Плагины

| Плагин | Что даёт |
|---|---|
| `office-files` | файловый менеджер офиса рядом с тредом |
| `markdown-view` | `.md` открывается во вкладке как документ, а не как код |
| `notify` | уведомления о работе агентов |
| `ayu` | палитра и темы ayu |
| `pets` | питомец в интерфейсе |
| `chime` | звук по событиям |

### Настройка office-files под конкретный офис

```bash
bb plugin config office-files set rootPath /home/<пользователь>/office
bb plugin config office-files set hostMatch <часть имени машины сервера>
bb plugin config office-files
```

`rootPath` — где лежит офис на сервере. `hostMatch` — кусок имени машины, по которому плагин
поймёт, какая из подключённых машин держит офис.

## Чего здесь нет

- Встроенные плагины BB (`tasks`, `automations`, `secrets`, `docs`, `github`, `workflows`
  и остальные) — они идут с приложением, ставить не нужно.
- `kanban` — стоял из локальной папки, репозитория нет; при необходимости ставится из каталога.
