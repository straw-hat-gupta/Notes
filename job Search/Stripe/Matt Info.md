

For integration round I think I didn’t even do tests 
They just asked how I WOULD test it 
And I didn’t use postman 
I think it’s probably too slow for me cus the api was pretty simple I just ran the code and iterated 
I don’t think they’ll stop u from using it if u like it more tho 

Did you have to write tests for the other two parts? Like for bug squash did you need to add more tests for the code you changed? Or for the coding exercise?

No test for bug squash 
For the integration I think I did have to
I wouldn’t personally practice pytest or magicmock 
They’ll be happy with assert statements 
It’s a lot of overhead to set up a proper unit test environment 
That being said you should aim to compose your code on the integration round such that it is easy to test 
For example, make a class that handles making the request header and body as well as extracting relevant output 
And the http client can be passed into the constructor instead of created by the constructor cuz then its makes it easy to mock the client with dependency injection
I think I also created helper function to create the request body cuz you’ll have to send many requests with slightly different parameters 

# probably worth creating a virtual environment when you kick things off,
# in case you want to import other libraries (i.e. json). Requests comes
# in the std-lib, so you'll be fine for that.

import requests
import json # optional, you'll need to `pip install` this

OUTPUT_FILE: str = "image.png"

class RequestHandler:
    BASE_URL = "..." # just pasted the base URL here

    def __init__(self, http_client):
        self.http_client = http_client
        # todo

    def build_request_body(self, **kwargs) -> dict:
        return {
            # I just copy pasted the example request body
            # and modified it from here.  
            #
            # I either used an f-string for templating, or
            # just passed the arguments in to create a dict
        }

    def save_output(self, resp_bytes):
        # something like this, maybe was "w" instead of write-binary. Can try both.
        with open(OUTPUT_FILE, "wb") as f:
            f.write(resp_bytes)
    
    def call(self, method, **kwargs) -> bytes:
        body = self.build_request_body(**kwargs)
        resp = self.http_client.post(self.BASE_URL + "/" + method, json=body)
        return resp.content

if __name__ == "__main__":
    handler = RequestHandler(requests)
    raw_output = handler.call("endpoint1", **{"foo": 1, "bar": "baz"})
    handler.save_output(raw_output)

