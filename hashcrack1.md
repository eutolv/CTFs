content: |
  # 🔐 picoCTF - Cracking Hash Challenge

  ---

  ## 🕵️‍♂️ Desafio

  Um servidor armazenou uma mensagem secreta, mas o administrador usou senhas com hashes fracas.  
  Seu objetivo? Quebrar essas hashes para descobrir as senhas e, no final, a flag secreta! 🚀

  ---

  ## 🧩 Hashes apresentadas

  | Hash                                                                 | Tipo    |
  |----------------------------------------------------------------------|---------|
  | `482c811da5d5b4bc6d497ffa98491e38`                                  | MD5     |
  | `b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3`                         | SHA1    |
  | `916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745` | SHA256  |

  ---

  ## 🛠️ Ferramentas utilizadas

  - **John the Ripper** – o clássico quebra-hash  
  - **Wordlist rockyou.txt** – disponível no Kali Linux em `/usr/share/wordlists/rockyou.txt`

  ---

  ## 📚 Passo a passo para quebrar as hashes

  1. **Criar arquivo com a hash:**

      ```bash
      echo "HASH_A_QUEBRAR" > hash.txt
      ```

  2. **Rodar John the Ripper com o formato correto:**

      - Para MD5:

        ```bash
        john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
        ```

      - Para SHA1:

        ```bash
        john --format=raw-sha1 --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
        ```

      - Para SHA256:

        ```bash
        john --format=raw-sha256 --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
        ```

  3. **Verificar as senhas descobertas:**

      ```bash
      john --show hash.txt
      ```

  ---

  ## 🎉 Resultados obtidos

  | Hash                                                                   | Tipo   | Senha encontrada      |
  |------------------------------------------------------------------------|--------|----------------------|
  | `482c811da5d5b4bc6d497ffa98491e38`                                   | MD5    | password123          |
  | `b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3`                          | SHA1   | [senha descoberta]    |
  | `916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745`  | SHA256 | [senha descoberta]    |

  ---

  ## 🏁 Flag final

### picoCTF{UseStr0nG_h@shEs_&PaSswDs!_29028be8}


---

## ⚠️ Observações

- Senhas fracas e hashes fracas = 💥 desastre na segurança!  
- Sempre use senhas fortes e algoritmos de hash robustos!  
- Wordlists são poderosas aliadas para quebrar essas proteções — invista tempo em boas listas!
