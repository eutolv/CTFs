# 🧠 Desafio CTF – Forense com `disko-1.dd.gz` (picoCTF)

> **Categoria:** Forensics  
> **Fonte:** [picoCTF](https://play.picoctf.org)  
> **Dica dada:** _"Maybe Strings could help? If only there was a way to do that?"_

---

## 🧩 Enunciado

Foi fornecido um arquivo chamado `disko-1.dd.gz`.  
A missão era encontrar uma flag escondida dentro dele.

---

## 🛠️ Passo a Passo

### 1. 🔓 Descompactar o arquivo `.gz`

```bash
gzip -d disko-1.dd.gz
```

> Isso gera o arquivo `disko-1.dd`, uma imagem de disco bruta.

---

### 2. 🧭 (Opcional) Montar a imagem

<details>
<summary>Caso queira explorar o sistema de arquivos</summary>

```bash
sudo mkdir /mnt/disko
sudo mount -o loop disko-1.dd /mnt/disko
ls /mnt/disko
```

> Montar a imagem permite navegar como um sistema Linux normal, mas **nenhuma flag foi localizada dessa forma neste desafio**.
</details>

---

### 3. 🧵 Seguindo a dica: usar `strings`

A dica sugeria extrair texto legível. Então...

```bash
strings disko-1.dd | grep -Eo 'picoCTF\{[^}]+\}'
```

🎯 **Resultado:**
```txt
picoCTF{1t5_ju5t_4_5tr1n9_be6031da}
```

---

## 🤯 Por que isso funcionou?

Montar o disco só mostra os dados do sistema de arquivos ativo.

Mas ao rodar `strings` na imagem `.dd`, o comando lê **todo o conteúdo bruto do disco**, incluindo:

- arquivos deletados (ainda não sobrescritos),
- espaço não alocado,
- fragmentos de memória ou logs,
- dados não referenciados diretamente por pastas.

Essa técnica é comum em investigações forenses reais.

---

## ✅ Conclusão

Nem sempre a flag está num arquivo visível.

Neste exercício, a flag estava escondida no **conteúdo bruto do disco**, e `strings` foi a chave.  
Montar o disco não era necessário, mas serviu de prática útil — especialmente para quem está estudando **LPIC** ou fundamentos de Linux.

---

## 🧠 Aprendizados

- `strings` é uma ferramenta forense extremamente útil.
- Ao lidar com `.dd`, sempre tente primeiro:  
  ```bash
  strings imagem.dd | grep pico
  ```
- Montar imagens é útil, mas pode não revelar tudo.
- Forense digital é tanto sobre ferramentas quanto **raciocínio estratégico**.

---

📁 *Este desafio faz parte da minha trilha de aprendizado em segurança e análise forense com CTFs.*  
🔗 Repositório: [github.com/eutolv](https://github.com/eutolv)
