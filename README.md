# Melanoma detection API
Serves a deep learning based melanoma detection model using a REST API endpoint.

### Local development
To use this code for local dev, first clone the repo using :
```bash
$ git clone https://github.com/hasibzunair/adversarial-lesions-rest-api-demo.git
```

Then navigate to the project folder and install the requirements using (make sure Python version is 3.6):
```bash
$ cd adversarial-lesions-rest-api-demo
$ pip install -r requirements.txt
$ pip install -i https://test.pypi.org/simple/ melanet
```
Now, you're setup!

### Usage

To launch the API server run:
```bash
$ python server.py
```
A fastapi app will run on your local machine. See Swagger UI at `http://127.0.0.1:8000/docs` for more info.
To interact with it, open a new terminal and just send a curl request like this (make sure you are in the project folder):
```bash
$ curl -X POST -F image=@test.jpg "http://127.0.0.1:8000/api/predict"
```

Using the `test.jpg` image, the JSON response result should look like this, with labels and the probability values:
```json
{
  "success": true,
  "predictions": [
    {
      "label": "Non-melanoma",
      "probability": 0.9180707335472107
    },
    {
      "label": "Melanoma",
      "probability": 0.08192921429872513
    }
  ]
}
```

Or, submit a request using Python like this:
```bash
$ python request.py
```
The result should look like this:
```bash
1. Non-melanoma: 0.9181
2. Melanoma: 0.0819
```

To try it with any of your own images(`*.jpg`,`*.jpeg`,`*.png`), set path to your image `YOUR_IMG_PATH` and run:
```bash
$ curl -X POST -F image=@YOUR_IMG_PATH "http://127.0.0.1:8000/api/predict"
```

### Relevant materials
* Training code for the detection model: [https://github.com/hasibzunair/adversarial-lesions](https://github.com/hasibzunair/adversarial-lesions)
* Web application demo can be found at [https://aiderm.herokuapp.com/](https://aiderm.herokuapp.com/)
* Source code for web app demo: [https://github.com/hasibzunair/melanoma-detection-demo](https://github.com/hasibzunair/melanoma-detection-demo)

### License
MIT