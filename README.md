# Latent Consistency LoRAs with BentoML

This repository demonstrates how simple it is to deploy a REST API server for stable diffusion with minimal inference steps. We'll use BentoML to convert [this HuggingFace example](https://huggingface.co/blog/lcm_lora) for Latent Consistency LoRAs!

# Try it out!

1. Install the required dependencies:
```
pip install -r requirements.txt
```

2. Serve the model as an HTTP server, which will bind port 3000. You can access the service at http://127.0.0.1:3000.
```
bentoml serve .
```

3. Generate an image with text prompt through "Try it Out" at http://127.0.0.1:3000 or using a curl request:
```
curl -X 'POST' \
  'http://localhost:3000/txt2img' \
  -H 'accept: image/*' \
  -H 'Content-Type: application/json' \
  -d '{
  "prompt": "close-up photography of old man standing in the rain at night, in a street lit by lamps, leica 35mm summilux"
}' -o out.jpg
```

And that's it! Next, you can run `bento build` and choose between [deploying your model to BentoCloud](https://docs.bentoml.com/en/latest/bentocloud/getting-started/quickstart.html) or containerizing the service with Docker.
