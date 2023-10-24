# Polyalphabetic-Chipper

Nama    : Ilham Maulana Cakra Dwi Noto
NIM     : 312110027
Kelas   : TI.21.A.1

<h1>Perkenalan</h1>

Polyalphabetic cipher bekerja dengan mengganti setiap huruf dalam pesan asli dengan satu atau lebih huruf pengganti berdasarkan aturan tertentu. Sebagai contoh, salah satu teknik penyandian polialfabetik yang paling terkenal adalah Cipher Vigenère, yang menggunakan kata kunci sebagai panduan untuk mengganti huruf-huruf dalam pesan. Setiap huruf dalam kata kunci digunakan untuk mengganti huruf dalam pesan, dan jika kata kunci lebih pendek dari pesan, kata kunci akan diulang.

berikut kodingan sekaligus input plaintext dan key nya

```php
def generate_key(keyword, message_length):
    keyword = keyword.lower().replace(" ", "")  # Mengonversi ke huruf kecil dan menghapus spasi
    alphabet = 'abcdefghijklmnopqrstuvwxyz'
    key = ""
    keyword_index = 0

    for i in range(message_length):
        char = keyword[keyword_index]
        if char not in key:
            key += char
        keyword_index = (keyword_index + 1) % len(keyword)  # Menggunakan modulo untuk melingkupi kunci jika pesan lebih panjang dari kunci
    
    for char in alphabet:
        if char not in key:
            key += char
    
    return key

def polyalphabet_cipher(plaintext, keyword):
    alphabet = 'abcdefghijklmnopqrstuvwxyz'
    plaintext = plaintext.replace(" ", "").lower()
    key = generate_key(keyword, len(plaintext))
    ciphertext = ""
    
    for i in range(len(plaintext)):
        char = plaintext[i]
        if char in alphabet:
            char_index = alphabet.index(char)
            shifted_char = key[char_index]
            ciphertext += shifted_char
        else:
            ciphertext += char
    
    return ciphertext.upper()

# Contoh penggunaan
plaintext = "BELAJAR KRIPTOGRAFI"
keyword = "MERDEKA"
ciphertext = polyalphabet_cipher(plaintext, keyword)
alphabet = "abcdefghijklmnopqrstuvwxyz"
hasil = keyword + alphabet
result = " ".join(dict.fromkeys(hasil))  # Hapus karakter yang sama
print(result)
print("Plaintext     :", plaintext)
print("Kunci          :", keyword)
print("Ciphertext    :",ciphertext)

```
Sekian Terima Kasih
