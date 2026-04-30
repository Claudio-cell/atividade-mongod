# Atividade MongoDB - CRUD com mongosh

Aluno: Claudio Neto 
RA:6325101
Data: 29/04/2026

# criar um banco 
use loja_virtual

# criar coleção 
db.createCollection("produtos")

# Inserir um produto com insertOne()

db.produtos.insertOne({
  nome: "Smartphone Galaxy A15",
  categoria: "Eletronicos",
  preco: 1299.90,
  marca: "Samsung",
  armazenamento: "128GB",
  cor: "Azul"
})

# Inserir múltiplos produtos com insertMany()

db.produtos.insertMany([
  {
    nome: "MongoDB na Pratica",
    categoria: "Livros",
    preco: 79.90,
    autor: "Joao Silva",
    editora: "Tech Books",
    paginas: 320
  },
  {
    nome: "Camiseta Basica",
    categoria: "Roupas",
    preco: 49.90,
    tamanho: "M",
    cor: "Preta",
    material: "Algodao"
  },
  {
    nome: "Notebook Ultra X",
    categoria: "Eletronicos",
    preco: 3899.90,
    marca: "Lenovo",
    memoria_ram: "16GB",
    processador: "Intel i7"
  },
  {
    nome: "Tenis Runner Pro",
    categoria: "Calcados",
    preco: 299.90,
    tamanho: 42,
    cor: "Branco",
    marca: "Olympikus"
  }
])

# Exercício 2: Consultas e Filtros (READ)
Listar todos os produtos

db.produtos.find()

//Produtos com preço superior a 100

db.produtos.find({ preco: { $gt: 100 } })

# Produtos da categoria Eletronicos 

db.produtos.find({ categoria: "Eletronicos" })

# Retornar apenas nome e preço

db.produtos.find({}, { nome: 1, preco: 1, _id: 0 })

# Exercício 3: Atualização Dinâmica (UPDATE)
Atualizar o preço de um produto

db.produtos.updateOne(
  { nome: "Smartphone Galaxy A15" },
  { $set: { preco: 1199.90 } }
)

# Adicionar campo estoque para todos os produtos

db.produtos.updateMany(
  {},
  { $set: { estoque: 50 } }
)

# Marcar produtos da categoria Roupas em promoção

db.produtos.updateMany(
  { categoria: "Roupas" },
  { $set: { promocao: true } }
)

# Exercício 4: Exclusão de Dados (DELETE)
Remover um produto específico

db.produtos.deleteOne({
  nome: "MongoDB na Pratica"
})

# Remover todos os produtos da categoria Calcados

db.produtos.deleteMany({
  categoria: "Calcados"
})

