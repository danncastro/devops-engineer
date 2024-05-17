# Configurações iniciais

### **Configura usuário**
~~~bash
git config --local user.name "user"
~~~
~~~bash
git config --global user.name "user"
~~~

#### **Lista usuário configurado**
~~~bash
git config user.name
~~~

---
### **Configura email do usuário**
~~~bash
git config --local user.email  "email"
~~~
~~~bash
git config --global user.email "email"
~~~

#### **Lista email configurado**
~~~bash
git config user.email
~~~

---
### **Define editor padrão**
~~~bash
git config --global core.editor "editor"
~~~
#### **Lista editor configurado**
~~~bash
git config core.editor
~~~

---
### **Define uma branch como padrão**
~~~bash
git config --global init.defaultBranch 'branch'
~~~

---
### **Configura alias**
~~~bash
git config --global alias.s 'alias'
~~~
#### **Lista as alias configuradas**
~~~bash
git config alias.s
~~~

---
### **Lista todas as informações cadastradas**
~~~bash
git config --list
~~~

---
### **Criar repositório remoto pela linha de comando**
~~~bash
echo "# nome-repositio" >> README.md
git init
git add README.md
git commit --m "Comentario"
~~~

---
### **Verifica se há repositorios remotos conectados**
~~~bash
git remote 
~~~

### **Conectando repositório local ao remoto**
~~~bash
git remote add origin git@github.com:email/nome-repositorio.git
~~~

---
### **Unir duas branchs*
~~~bash
git rebase nome-branch
~~~

