# Oasis Writeup

## Heads up, tails down

### This challenge taught me about file headers

Challenge: A corrupted png was given and we had to fix it to get the flag

Approach: Fix the file header to that of a normal png file using some hex editor

## Not Noice

### This challenge taught me about audio spectral analysis

Challenge: An audio file was given and we had to find the flag hidden within it

Approach: Using a spectrogram we can get what the audio file looks like when plotten on a graph, from there the flag was found

## Nom-Nom

### This challenge taught me about cookies

Challenge: A website says it'll only give the flag to the admin

Approach: Set admin=true in cookies and it'll give the flag

## All that for a drop of blood

### This challenge taught me about user agents and post requests

Challenge: Given is a site which says "You need to be OASISPlayer to start the game"

Approach: 

1. "You need to be OASISPlayer to start the game" message indicates we have to set user-agent as "OASISPlayer"
2. Upon doing that we are given a message "Can you give me the name of the Student Project organizing this event as a url parameter 'name'?"
3. Simply typing "https://startgame.oasis.cryptonite.live/game?name=cryptonite" in the url section in browser won't work since that sends a GET request that means we are supposed to send a POST request
4. Send a post to the /game endpoint:

    ```python
    import requests
    r = requests.post("https://startgame.oasis.cryptonite.live/game?name=cryptonite")
    print(r.text)
    ```
    This gives an error message:

    ```
    {"errorMessage":"Do you know you can chain query parameters? Add a 'rank' parameter and give the current CTFTime rank of the project on /givemetheFlag"}
    ```
5. This means now we have to send a POST request to the /givemetheFlag endpoint with name=cryptonite&rank=4

    ```python
    import requests
    r = requests.post("https://startgame.oasis.cryptonite.live/givemetheFlag?name=cryptonite&rank=4",headers = {'User-Agent': 'OASISPlayer'})
    print(r.text)
    ```
    This gives us the flag:
    ```
    {"Flag":"OASIS{G37_d035_n07_4lw4y5_G37_th1ng5}"}
    ```