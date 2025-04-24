
# 🐳 DDEV Setup - Projetos PHP, Laravel, Node.js/React + MySQL

Este guia contém os comandos essenciais para configurar projetos usando DDEV com diferentes stacks de desenvolvimento.

---

## 📦 Requisitos

- Docker Desktop (com WSL2 ativado)
- DDEV instalado globalmente (`choco install ddev -y` ou via instalador)
- Git Bash, PowerShell ou terminal WSL

---

## 🔹 PHP + MySQL + Composer

```bash
mkdir meu-projeto-php && cd meu-projeto-php
ddev config --project-type=php --docroot=public
ddev start
```

> 🔧 A pasta `public` será criada automaticamente. Adicione seus arquivos PHP dentro dela.

### Banco de dados

- Host: `db`
- Usuário: `db`
- Senha: `db`
- Database: `db`

### PHPMyAdmin (opcional)

```bash
ddev add-on get ddev/ddev-phpmyadmin
ddev restart
```

---

## 🔹 Laravel + MySQL

```bash
mkdir meu-projeto-laravel && cd meu-projeto-laravel
ddev config --project-type=laravel --docroot=public
ddev start
ddev composer create laravel/laravel .
```

### Após instalar:

```bash
ddev exec php artisan migrate
ddev launch
```

---


## 🔹 Apenas Banco de dados MySQL + phpmyadmin

```bash
ddev config --project-type=php --docroot=. --create-docroot
ddev start
```

### Após instalar:

```bash
ddev phpmyadmin

```

---

## 🧹 Como remover um projeto DDEV

```bash
ddev stop
ddev delete --omit-snapshot
rm -r .ddev
```

---

## 📁 Organização sugerida

```
/Projetos
  ├── meu-projeto-php
  ├── meu-projeto-laravel
  ├── node-api
  └── react-app
```

---

## ✅ Dicas

- Use `ddev describe` para ver detalhes do projeto atual
- Use `ddev launch` para abrir no navegador
- Todos os projetos podem compartilhar o mesmo servidor MySQL interno do DDEV

---
