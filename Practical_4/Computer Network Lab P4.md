**Computer Network lab**

**Name: Ayush Ravindra Patil**

**Date: 10-09-26**

**Practical: 4**

**1\] CRC (Cyclic Redunduncy Check):**

> **\# Algorithm:**
>
> **Step 1) Start**
>
> **Step 2) Take input dataword and polynomial**
>
> **Step 3) Convert the polynomial into bits and calculate the number of redundancy bits (zeros). **
>
> **Step 4) Concatenate the dataword and the redundancy bits (zeros) to create the padded dataword. **
>
> **Step 5) Perform Modulo-2 Division (also known as XOR division) on the sender side with the padded dataword and the divisor. **
>
> **Step 6) Concatenate the resulting remainder at the LSB (Least Significant Bit) with the original dataword to form the codeword. **
>
> **Step 7) Perform Modulo-2 Division (XOR division) on the receiver side with the received codeword and the divisor. **
>
> **Step 8) If the remainder is 0, then the data is accepted; otherwise, discard the operation (error detected). **
>
> **Step 9) Stop**

**2\] Code:**

```python
def xor_division(bits, generator):
    data = list(bits)
    gen = list(generator)
    # Loop through the data string up to the point where the generator fits
    for i in range(len(data) - len(gen) + 1):
        # In Modulo-2, we only XOR if the leading bit of the current window is '1'
        if data[i] == '1':
            for j in range(len(gen)):
                # Perform XOR logic on the current window of bits
                data[i + j] = str(int(data[i + j]) ^ int(gen[j]))
                
    # Return the remaining bits (the remainder)
    return ''.join(data[-(len(gen) - 1):])
  
print("Sender's side")
dataword = input("Enter dataword bits: ")    
generator = input("Enter generator bits: ")
print("\nDataword :", dataword)
print("Generator:", generator)

zeros = '0' * (len(generator) - 1)
padded_data = dataword + zeros
print("Padded data : ", padded_data)

crc = xor_division(padded_data, generator)
print("CRC         :", crc)

codeword = dataword + crc
print('Codeword    :', codeword)

print("\nReceiver's Side:")
received = input("Enter received bits: ")
receiver_remainder = xor_division(received, generator)
print("Receiver remainder:", receiver_remainder)

if receiver_remainder == '0' * (len(generator) - 1):
    print("Result: no error detected")
else:
    print("Result: error detected")
```

**3\] Output:**

- **If Correct:**

> ![](./images/image1.png)

- **If Incorrect:**

> ![](./images/image2.png)
