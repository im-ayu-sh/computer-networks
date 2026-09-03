**Computer Network lab**

**Name: Ayush Ravindra Patil**

**Date: 27-08-26**

**Practical: 1**


---


**1] Bit Stuffing**

**Code:**

```python
def bit_stuffing(data):

    flag = '01111110'

    pattern = '111111'

    stuffed_bit='0'

    stuffed_data = ''

    count=0

    for bit in data:

        if bit=='1':

            count_ones += 1

            stuffed_data += bit

        else:

            count_ones = 0

            stuffed_data += bit

        if count_ones == 5:

            stuffed_data += stuffed_bit

            count_ones = 0

        return flag + stuffed_data + flag

data = '01111011111101110'

print(f'Original data: {data}')

print(f'stuffed bit: {bit_stuffing(data)}')
```

**Output:**

<img src="./imagesimage1.png"
style="width:3.60467in;height:1.40645in" />


---


**2] Character Stuffing**

**Code:**

```python
def character_stuffing(data):

    flag = 'F'

    esc = 'E'

    stuffed_data = ''

    for char in data:

        if char == flag or char == esc:

            stuffed_data += esc

        stuffed_data += char

    return flag + stuffed_data + flag

data=input("Enter character frame: ")

print(f'Original Data: {data}')

print(f'Stuffed Data: {character_stuffing(data)}')
```

**Output:**

<img src="./images/image2.png"
style="width:4.22917in;height:1.52083in" />
