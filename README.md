# ha-ihost
Call API Sonoff iHost from Home Assistant 

This code is usefull to call funtions by API Rest.

💡GOAL: Ativate iHOST speaker from Home Assistant
-- When the HA alarm is active and there is detection on one of the sensors, the iHost will play an alarm on the speaker.

😎 PRÉ-requirement: Home Assistant (acess configuration.yaml) and Sonoff iHost API
-- rest_command

🍽️ HOW TO DO IT: Edit your configuration.yaml from Home Assistant
-- Use de RESTful Command to call API with JSON parameters:
--- Use your Token from iHost and put on Authorization header with "Bearer" 
```
rest_command:
  play_speaker_sound_alarm:
    url: "http://YOUR iHOST IP/open-api/v1/rest/hardware/speaker"
    method: POST
    headers:
      Content-Type: application/json
      Authorization: "Bearer 1795590-b286-xxxx-9c6d-321xxzxx16743"
    payload: >
      {
        "type": "play_sound",
        "sound": {
          "name": "alert5",
          "volume": 100,
          "countdown": 10
        }
      }
```
⚽ THE Speaker will play for 10 seconds using de type Alert5
-- You can change time; volume and type of alert;
--- Call action: rest_command.play_speaker_sound_alarm in automation for ex.
