# apns2-client

apns2-client is a python package designed for simple, flexible and fast Apple Push Notifications on iOS, OSX and Safari using the new HTTP/2 Push provider API.

## Features

- Uses new Apple APNs HTTP/2 connection
- Supports new iOS 10 features such as Collapse IDs, Subtitles and Mutable Notifications
- Supports persistent connections to APNs
- Fast, modular & easy to use
- Tested and working in APNs production environment

## Cautions

- Works only with Python 3.5 and later

## Install

- Make sure you have [pip](https://pip.pypa.io/en/stable/installing/) installed.
- Install `apns2-client`:

  ```sh
  pip install apns2-client
  ```

## Example

```python
from apns2 import APNSClient, Notification, Payload, PayloadAlert


cli = APNSClient(mode="dev", client_cert="/your/path.pem")
alert = PayloadAlert(body="body!", title="title!")
payload = Payload(alert=alert)
n = Notification(payload=payload, priority=5)
response = cli.push(n=n, device_token="your_token")
assert response.status_code == 200, response.reason
assert response.apns_id
```