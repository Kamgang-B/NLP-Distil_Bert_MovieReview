## Distil_Bert_MovieReviwe

### Sentiment Analysis based on movie reviwes 

#### Run app.py

Test the model 

import ktrain
predictor = ktrain.load_predictor('distilbert')
data = ["this movie is really great.deserves a lot of praises"]
predictor.predict(data)
['pos']

host = 'localhost'
port = 5000

url = "http://localhost:5000/"

x = requests.get(url)
print(x)
print(x.text)
<Response [200]>
Congrats ! server is working

url = "http://localhost:5000/"
data = {'Review': 'This movie is great. I have enjoyed a lot'}
data = json.dumps(data)

#### Positive 
url = "http://localhost:5000/get_sentiment"
x = requests.post(url,data)
print(x)
print(x.text)
<Response [200]>
{
  "result": "pos"
}

#### Negative
url = "http://localhost:5000/get_sentiment"
data = {'Review': 'This movie is horrible. Please return my money'}
data = json.dumps(data)
x = requests.post(url,data)
print(x.text)
{
  "result": "neg"
}

### Predict from Ec2 instance
# 54.234.249.222
url = "http://54.234.249.222:5000/get_sentiment"
data = {'Review': 'This movie is horrible. Please return my money'}
data = json.dumps(data)
x = requests.post(url,data)
print(x.text)
{
  "result": "neg"
}

The EC2 instance was terminated so above link does not work
