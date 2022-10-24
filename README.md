<div align="center">
  <h1> TWFileNameMaker </h1>
  <i> Dit programma maakt de bestandsnaam voor TW.</i>
    <div align="center">
      ![image](https://user-images.githubusercontent.com/46261961/197585901-159987d3-2c09-4412-866e-ec472661c563.png)
    </div>
</div>

## Docs

You can read the docs on this Git's Wiki, or [here](https://ms7m.github.io/notify-py/)

## Supported Platforms.

- Windows 10/11
- macOS 10 >=10.10
- Linux (libnotify)

No dependencies are required other than loguru & jeepney (Only for linux/DBUS).

---

## Install

```
pip install notify-py
```

---

## Usage

**Send Simple Notification**

```python
from notifypy import Notify
notification = Notify()
notification.title = "Cool Title"
notification.message = "Even cooler message."
notification.send()
```

**Send Notification With Icon**

```python
from notifypy import Notify
notification = Notify()
notification.title = "Cool Title"
notification.message = "Even cooler message."
notification.icon = "path/to/icon.png"
notification.send()
```

**Send Notification With Sound**

```python
from notifypy import Notify
notification = Notify()
notification.title = "Cool Title"
notification.message = "Even cooler message."
notification.audio = "path/to/audio/file.wav"
notification.send()
```

**Sending Notifications without blocking**

```python
from notifypy import Notify
notification = Notify()
notification.send(block=False)
```

**Sending with Default Notification Titles/Messages/Icons**

```python
from notifypy import Notify
notification = Notify(
  default_notification_title="Function Message",
  default_application_name="Great Application",
  default_notification_icon="path/to/icon.png",
  default_notification_audio="path/to/sound.wav"
)
def your_function():
  # stuff happening here.
  notification.message = "Function Result"
  notification.send()
```

---

# CLI
A CLI is available when you install notify-py

```bash
notify-py --title --message --applicationName --iconPath --soundPath
```
You may need to add ``python3 -m`` to the beginning.

---

## Important Caveats

- As it stands (May 18, 2020), this is simply a notification service. There is _no_ support for embedding custom actions (buttons, dialogs) regardless of platform. Other then telling you if the shell command was sent, there is also no confirmation on user action on the notification.

- macOS does **not** support custom icons on the fly.. You will need to bundle a customized version of the notifier embedded with your custom icon.

---

### Windows Specific.

- No support for balloon tips (pre Win10).. This will be changed in the future.

---

### Contributors

- [Leterax](https://github.com/Leterax)
- [jnoortheen](https://github.com/jnoortheen)
- [dynobo](https://github.com/dynobo)

---

### Inspiration and Special Thanks

- https://github.com/go-toast/toast - Ported their Windows 10 toast notification to Python.

- [Vítor Galvão](https://github.com/vitorgalvao) for https://github.com/vitorgalvao/notificator

- https://notificationsounds.com/notification-sounds/done-for-you-612 example_notification_sound.wav

- https://github.com/mikaelbr/node-notifier

---

# Contributing

Contributions are welcome!

Please base your changes on the latest development branch and open a PR to that branch. PR will not be accepted to the master branch. Tests are ran against all platforms.

### Setting Up Environment

- Install [Poetry](https://python-poetry.org/)
  - `poetry install`
- Add patches/new features/bug fiexes
- Run tests
  - `poetry run pytest tests/*`
- Run lints
  - `poetry run pylint --errors-only notifypy/`
- Run Black Formatting
  - `poetry run black notifypy`
- Open PR to `dev` branch.
- Add your name to contributors list if you wish!
