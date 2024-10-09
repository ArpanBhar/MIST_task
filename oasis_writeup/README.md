# Oasis Writeup

## Keanu crack the matrix

### This challenge taught me how negative modding with large numbers makes it behave like simple subtraction

Challenge: A matrix was given with many seemingly random numbers, an encryption code was also given, we had to make a decryption code and decrypt it.

Approach: 

1. Looking at the decryption code, we can find that if i ≠ j, the negative values of the number array are modded with the primes, we also know the string length is 36 since there are 36 columns in the matrix
2. Since negative mod with large numbers behaves like simple subtraction, we can retrieve the original primes by regenerating the number array and using the same i ≠ j condition but this time we subtract the negative values of the array
3. After retrieving the keys we can subtract the encrypted number from the key to get the original ascii values
4. Convert the ascii values to get the characters which give the flag

Code:

```python
string_len = 36
num_array = []
keys=[]
for i in range(1,string_len*string_len+1,string_len):
    num_array.append([((-1)*j) for j in range(i,i+string_len)])

with open(r"C:\Users\ARPAN BHAR\Desktop\OASIS_27\out.txt","r") as f:
    encrypted_matrix = eval(f.read())
for i in range(string_len-1):
    keys.append(encrypted_matrix[i][i+1] - num_array[i][i+1])
keys.append(encrypted_matrix[35][34]-num_array[35][34])
for i in range(string_len):
    print(chr(keys[i]-encrypted_matrix[i][i]),end="")
```

Flag: `OASIS{Bro_Really_Modded_It_Negative}`

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