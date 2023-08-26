# rasa-form-tutorial
Goes with my article about rasa forms (pt 1)


## Quickstart for rasa server

1. use python3.8 or python3.9 (virtualenv or conda environment *strongly* recommended)
2. `pip install -r requirements.txt`
3. `rasa train`
4. `rasa run -p <PORT>` OR `rasa shell -p <PORT>`


## Rasa server http interface


Client code:

```
CHATBOT = "http://localhost:5005/webhooks/rest/webhook"

payload = '{"sender": "' + user + '", "message": "' + message + '"}'
r = requests.post(CHATBOT, data=payload.encode('utf-8'))

response = json.loads(r.content)
```

### Request data json
``` 
{"sender": str, "message": str}
```

Field "sender" holds a conversation id that is made on the client side on each new session.


### Response data json
```
[{"recipient_id": str, "text":str}]
```

Field "Recipient_id" holds the same value as "sender" value of the request.
