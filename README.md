# gridlock
Encryption and decryption of plain text messages inspired by the Gaussian curve method of blurring images and the Caesar Cipher.

## How it works

### The shuffle
To better encrypt our message, we have a tuple (non-editable list) of characters available. This is then assigned to a new List which is then shuffled using the shuffle() function. Each encryption gets a new shuffle, making the combinations equal to the Factorial of the list length.

### The line-length
The code then generates a random number that will be used for the line length of your message, which will be stored in a list of lists.

For example, if we want to encrypt the message `Hello World!` and the application randomly selects `5` for the line length, it will store it in a list in this format:
```
[['H'], ['e'], ['l'], ['l'], ['o']
 [' '], ['W'], ['o'], ['r'], ['l']
 ['d'], ['!']]
```

This method add an extra variable to the security of the message by the way the grid traverses our message to be encrypted.

### The grid
The grid is where I was inspired by the way Gaussian blur work. Taking information from around the character to be encrypted and performing some algorithm and assigning that new `key` to our shuffled list.

![Grid represented](https://github.com/uxai/gridlock/blob/main/images/grid.jpg)

For each character that is preceding (purple) the current target (orange), the shuffled list will be referenced. For all characters ahead of the current target, the original tuple will be referenced for their key index.

#### Modifying the grid
The grid by default is a 3x3, represented by variables grid_height and grid_width in range format. This is just another variable you may use to strengthen the complexity of the encryption. Change the shape to a rectangle, offset the center, and much more.

#### Void spaces
Any space that is empty on the grid is another mode of enforcement, where void spaces are assigned a random digit - any void spaces will be valued with this digit.

### Index offset
After all the calculations are completed, there is one more offset - another random number, to offset the index. Just one more mode of security.

## Example output
This output will give you everything you need to decrypt the message. Of course, if you lose it - you will never be able to recover the message.
```
Type or paste the message to be encrypted:
Hello World!

SECRET KEYS
Save the following information in a safe place.
------------
ALPHA KEY:
iX1£xIYw?cdea#*t/Wr¥(L|bG!q3~AJn^D-=,"9g7&+`p_8)BH'Ohf0V@m}FSs:zKlo%>$MR.k5Q\jvEZ{ U4P6N[C;<uy]2T
------------
INDEX OFFSET:  57
LINE LENGTH:   12
VOID SPACES:   9
GRID HEIGHT:   range(-1, 2)
GRID WIDTH:    range(-1, 2)

Your encrypted message:
Sp=A (TTy\P5
```

## Decryption
When decrypting, it will ask for all the information given in the output - after inputing you will get a response in the similar fashion:

```
What is the index offset? 57
What is the line length? 12
What is the value of void spaces? 9
What is the height of your grid? for example: -1, 2: -1, 2
What is the width of your grid? for example: -1, 2: -1, 2
Type or paste the message to be decrypted:
Sp=A (TTy\P5

What is your alpha key?
iX1£xIYw?cdea#*t/Wr¥(L|bG!q3~AJn^D-=,"9g7&+`p_8)BH'Ohf0V@m}FSs:zKlo%>$MR.k5Q\jvEZ{ U4P6N[C;<uy]2T

Your decrypted message is:
Hello World!
```

If we try to do the same decryption, but one digit is off, for example the value of void spaces, you will see a garbage output like the following:
```
Your decrypted message is:
HlksnGVvqsc*
```

## Foot notes
I do plan to update with allowing file selection in the future, and maybe easier customisation of the grid dimensions.

version 1.0
