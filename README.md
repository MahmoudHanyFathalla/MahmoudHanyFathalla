## Unfortunately, I am a passionate Software Engineer...

Great! Here's a detailed breakdown of how to complete your project on **Linux** step by step:

---

### 🧩 **Task 1: Image Encryption with AES-128**

#### 📌 Step 1: Choose your image

* Place your image in your project directory. Let's call it `input.png`.

#### 📌 Step 2: Generate a 128-bit AES key

```bash
openssl rand -hex 16 > aes.key
```

#### 📌 Step 3: Encrypt using AES in 4 modes (ECB, CBC, CFB, OFB)

> Note: AES in ECB mode may require padding.

##### **1. ECB Mode**

```bash
openssl enc -aes-128-ecb -in input.png -out encrypted_ecb.png -K $(cat aes.key) -nosalt
```

##### **2. CBC Mode**

```bash
openssl rand -hex 16 > iv_cbc.key
openssl enc -aes-128-cbc -in input.png -out encrypted_cbc.png -K $(cat aes.key) -iv $(cat iv_cbc.key) -nosalt
```

##### **3. CFB Mode**

```bash
openssl rand -hex 16 > iv_cfb.key
openssl enc -aes-128-cfb -in input.png -out encrypted_cfb.png -K $(cat aes.key) -iv $(cat iv_cfb.key) -nosalt
```

##### **4. OFB Mode**

```bash
openssl rand -hex 16 > iv_ofb.key
openssl enc -aes-128-ofb -in input.png -out encrypted_ofb.png -K $(cat aes.key) -iv $(cat iv_ofb.key) -nosalt
```

#### 📌 Step 4: View encrypted images

```bash
xdg-open encrypted_ecb.png
xdg-open encrypted_cbc.png
xdg-open encrypted_cfb.png
xdg-open encrypted_ofb.png
```

---

### 🧩 **Task 2: RSA Signature on Encrypted CBC Image**

#### 📌 Step 1: Generate RSA keys (2048 bits)

```bash
openssl genpkey -algorithm RSA -out private.pem -pkeyopt rsa_keygen_bits:2048
openssl rsa -pubout -in private.pem -out public.pem
```

#### 📌 Step 2: Hash the CBC encrypted image using SHA1

```bash
openssl dgst -sha1 -binary encrypted_cbc.png > hash.bin
```

#### 📌 Step 3: Create RSA Signature (sign the hash)

```bash
openssl dgst -sha1 -sign private.pem -out signature.bin encrypted_cbc.png
```

#### 📌 Step 4: Verify the signature

```bash
openssl dgst -sha1 -verify public.pem -signature signature.bin encrypted_cbc.png
```

> Output will be: `Verified OK` or `Verification Failure`

---

### 🌟 **Bonus: NIST Randomness Test**

#### 📌 Step 1–3: Setup

```bash
sudo apt-get update -y
sudo apt install python3-numpy python3-scipy
sudo apt-get install python3-tk
git clone https://github.com/stevenang/randomness_testsuite.git
cd randomness_testsuite
```

#### 📌 Step 4: Convert image files to binary for testing

Use this Python snippet:

```python
def img_to_bin(input_file, output_file):
    with open(input_file, "rb") as f:
        data = f.read()
    with open(output_file, "w") as f:
        for byte in data:
            f.write(f"{byte:08b}")

# Example usage:
img_to_bin("input.png", "input_binary.txt")
img_to_bin("encrypted_cbc.png", "cbc_binary.txt")
```

#### 📌 Step 5: Run the randomness test

```bash
python3 sts.py cbc_binary.txt
```

Repeat for each of:

* `encrypted_ecb.png`
* `encrypted_cfb.png`
* `encrypted_ofb.png`

#### 📌 Step 6: Comment on results

You'll see pass/fail for various statistical tests. More passes = better randomness. **OFB or CFB** usually perform better than ECB.

---

Would you like a ready-to-run bash or Python script for automating parts of this project?






<div id="header" align="center">
  <img src="https://i.pinimg.com/originals/da/0b/d7/da0bd7fff88a3e7f8df65e96327e9d87.gif" width="500"/>
</div>
<div id="badges" align="center">
  <a href="https://www.linkedin.com/in/mahmoud-hany-fathalla-6b1690219/">
    <img src="https://img.shields.io/badge/LinkedIn-blue?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn Badge"/>
  </a>
  <a href="https://www.instagram.com/mahmoud_hany_tms/">
    <img src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white" alt="Instagram"/><br>
  </a>
  <a href ="https://github.com/MahmoudHanyFathalla">
    <img src="https://komarev.com/ghpvc/?username=MahmoudHanyFathalla&style=flat-square&color=blue" alt=""/>
  </a>
  <br>
  <!-- GitHub Stars Badge (different style) -->
  <a href="https://github.com/MahmoudHanyFathalla">
    <img src="https://img.shields.io/github/stars/MahmoudHanyFathalla?style=flat-square&color=yellow" alt="GitHub Stars"/>
  </a>
</div>




- 🏠 Living in Cairo, Egypt
- 🏅 Interested in Competitive Programming
- 💻 Currently working as a software developer for RobEn's Software & AI team 
- 📫 How to reach me: **mahmoudhanyfathalla@gmail.com**

## 📊 GitHub Stats:



<br>


<div align="center">

<img height="158em" src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=MahmoudHanyFathalla&theme=radical">
<img height="158em" src="https://github-profile-summary-cards.vercel.app/api/cards/stats?username=MahmoudHanyFathalla&theme=radical">
<img height="160em" src="https://github-profile-summary-cards.vercel.app/api/cards/repos-per-language?username=MahmoudHanyFathalla&theme=radical">
<img height="160em" src="https://github-profile-summary-cards.vercel.app/api/cards/most-commit-language?username=MahmoudHanyFathalla&theme=radical">


</div><br>


<p align="center">
  <a href="https://github.com/ryo-ma/github-profile-trophy">
    <img src="https://github-profile-trophy.vercel.app/?username=MahmoudHanyFathalla&rank=SSS,SS,S,AAA,AA,A" alt="MahmoudHanyFathalla Trophies" />
  </a>
</p>

<h3 align="left">Languages and Tools:</h3>
<p align="center">
  <a href="https://github.com/ryo-ma/github-profile-trophy">
    <img src="https://github-profile-trophy.vercel.app/?username=MahmoudHanyFathalla&title=MultiLanguage" alt="MahmoudHanyFathalla Multi-Language Trophy" />
  </a>
</p>
<p align="left"> <a href="https://www.arduino.cc/" target="_blank" rel="noreferrer"> <img src="https://cdn.worldvectorlogo.com/logos/arduino-1.svg" alt="arduino" width="40" height="40"/> </a> <a href="https://www.gnu.org/software/bash/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/gnu_bash/gnu_bash-icon.svg" alt="bash" width="40" height="40"/> </a> <a href="https://www.cprogramming.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/c/c-original.svg" alt="c" width="40" height="40"/> </a> <a href="https://www.w3schools.com/cpp/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/cplusplus/cplusplus-original.svg" alt="cplusplus" width="40" height="40"/> </a> <a href="https://www.w3schools.com/cs/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/csharp/csharp-original.svg" alt="csharp" width="40" height="40"/> </a> <a href="https://www.w3schools.com/css/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original-wordmark.svg" alt="css3" width="40" height="40"/> </a> <a href="https://dart.dev" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/dartlang/dartlang-icon.svg" alt="dart" width="40" height="40"/> </a> <a href="https://www.djangoproject.com/" target="_blank" rel="noreferrer"> <img src="https://cdn.worldvectorlogo.com/logos/django.svg" alt="django" width="40" height="40"/> </a> <a href="https://www.docker.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg" alt="docker" width="40" height="40"/> </a> <a href="https://dotnet.microsoft.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/dot-net/dot-net-original-wordmark.svg" alt="dotnet" width="40" height="40"/> </a> <a href="https://flask.palletsprojects.com/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/pocoo_flask/pocoo_flask-icon.svg" alt="flask" width="40" height="40"/> </a> <a href="https://flutter.dev" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/flutterio/flutterio-icon.svg" alt="flutter" width="40" height="40"/> </a> <a href="https://git-scm.com/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="git" width="40" height="40"/> </a> <a href="https://www.w3.org/html/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg" alt="html5" width="40" height="40"/> </a> <a href="https://www.java.com" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" alt="java" width="40" height="40"/> </a> <a href="https://www.linux.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linux/linux-original.svg" alt="linux" width="40" height="40"/> </a> <a href="https://www.mongodb.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original-wordmark.svg" alt="mongodb" width="40" height="40"/> </a> <a href="https://www.mysql.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="mysql" width="40" height="40"/> </a> <a href="https://nodejs.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original-wordmark.svg" alt="nodejs" width="40" height="40"/> </a> <a href="https://opencv.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/opencv/opencv-icon.svg" alt="opencv" width="40" height="40"/> </a> <a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg" alt="pandas" width="40" height="40"/> </a> <a href="https://www.postgresql.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg" alt="postgresql" width="40" height="40"/> </a> <a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a> <a href="https://pytorch.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/pytorch/pytorch-icon.svg" alt="pytorch" width="40" height="40"/> </a> <a href="https://reactjs.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg" alt="react" width="40" height="40"/> </a> <a href="https://www.sqlite.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/sqlite/sqlite-icon.svg" alt="sqlite" width="40" height="40"/> </a> <a href="https://www.tensorflow.org" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/tensorflow/tensorflow-icon.svg" alt="tensorflow" width="40" height="40"/> </a> </p>

