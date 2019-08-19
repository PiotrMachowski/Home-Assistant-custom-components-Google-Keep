# Google Keep sensor

This sensor uses [*gkeepapi*](https://github.com/kiwiz/gkeepapi) to download a list of notes from [*Google Keep*](https://keep.google.com/).
 
## Configuration options

| Key | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `name` | `string` | `False` | `Google Keep` | Name of sensor |
| `username` | `string` | `True` | - | Username for Google Keep account |
| `password` | `string` | `True` | - | Password (or App Password) for Google Keep account |
| `titles` | `list` | `False` | `[]` | List of titles of notes to be imported |
| `labels` | `list` | `False` | `[]` | List of labels of notes to be imported |
| `pinned` | `boolean` | `False` | `False` | Activates downloaded limiting notes to pinned ones |

## Example usage

```
sensor:
  - platform: google_keep
    username: !secret google_keep.username
    password: !secret google_keep.password
    labels:
      - 'Home Assistant'
    pinned: true
```

## Hints

* To present data downloaded by this sensor use companion card: [*Lovelace Google Keep card*](https://github.com/PiotrMachowski/Lovelace-Google-Keep-card)

* If you define more than one constraint (`titles`, `labels`, `pinned`) all of them will be applied and intersection of results will be returned.

* **Do I have to use my Google Account password?**

  You can set up an App Password to use this component.
  * Go to [https://myaccount.google.com/apppasswords](https://myaccount.google.com/apppasswords)
  * In `Select app` menu choose `other` and provide your own identifier (e.g. `Home Assistant`)
  * Use generated password in sensor configuration (**Warning:** password will not be shown again!)

* **What to do if Home Assistant does not find this component?**

  Most likely you have to install additional dependency required for it to run. Activate Python environment Home Assistant is running in and use following command:
  ```bash
  pip install gkeepapi
  ```
