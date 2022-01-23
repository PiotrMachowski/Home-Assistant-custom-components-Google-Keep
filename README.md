[![HACS Default][hacs_shield]][hacs]
[![GitHub Latest Release][releases_shield]][latest_release]
[![GitHub All Releases][downloads_total_shield]][releases]
[![Community Forum][community_forum_shield]][community_forum]
[![Buy me a coffee][buy_me_a_coffee_shield]][buy_me_a_coffee]
[![PayPal.Me][paypal_me_shield]][paypal_me]


[hacs_shield]: https://img.shields.io/static/v1.svg?label=HACS&message=Default&style=popout&color=green&labelColor=41bdf5&logo=HomeAssistantCommunityStore&logoColor=white
[hacs]: https://hacs.xyz/docs/default_repositories

[latest_release]: https://github.com/PiotrMachowski/Home-Assistant-custom-components-Google-Keep/releases/latest
[releases_shield]: https://img.shields.io/github/release/PiotrMachowski/Home-Assistant-custom-components-Google-Keep.svg?style=popout

[releases]: https://github.com/PiotrMachowski/Home-Assistant-custom-components-Google-Keep/releases
[downloads_total_shield]: https://img.shields.io/github/downloads/PiotrMachowski/Home-Assistant-custom-components-Google-Keep/total

[community_forum_shield]: https://img.shields.io/static/v1.svg?label=%20&message=Forum&style=popout&color=41bdf5&logo=HomeAssistant&logoColor=white
[community_forum]: https://community.home-assistant.io/t/google-keep-custom-component-and-lovelace-card/131752

[buy_me_a_coffee_shield]: https://img.shields.io/static/v1.svg?label=%20&message=Buy%20me%20a%20coffee&color=6f4e37&logo=buy%20me%20a%20coffee&logoColor=white
[buy_me_a_coffee]: https://www.buymeacoffee.com/PiotrMachowski

[paypal_me_shield]: https://img.shields.io/static/v1.svg?label=%20&message=PayPal.Me&logo=paypal
[paypal_me]: https://paypal.me/PiMachowski

# Google Keep sensor

This sensor downloads a list of notes from [*Google Keep*](https://keep.google.com/).
 
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

## Installation

### Using [HACS](https://hacs.xyz/) (recommended)

This integration can be installed using HACS.
To do it search for `Google Keep` in *Integrations* section.

### Manual

To install this integration manually you have to download [*google_keep.zip*](https://github.com/PiotrMachowski/Home-Assistant-custom-components-Google-Keep/releases/latest/download/google_keep.zip) and extract its contents to `config/custom_components/google_keep` directory:
```bash
mkdir -p custom_components/google_keep
cd custom_components/google_keep
wget https://github.com/PiotrMachowski/Home-Assistant-custom-components-Google-Keep/releases/latest/download/google_keep.zip
unzip google_keep.zip
rm google_keep.zip
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

<a href="https://www.buymeacoffee.com/PiotrMachowski" target="_blank"><img src="https://bmc-cdn.nyc3.digitaloceanspaces.com/BMC-button-images/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: auto !important;width: auto !important;" ></a>
<a href="https://paypal.me/PiMachowski" target="_blank"><img src="https://www.paypalobjects.com/webstatic/mktg/logo/pp_cc_mark_37x23.jpg" border="0" alt="PayPal Logo" style="height: auto !important;width: auto !important;"></a>
