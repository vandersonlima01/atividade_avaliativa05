const express = require('express');
const mongoose = require('mongoose');

const app = express();
const port = 3000;

app.use(express.json());

mongoose.connect('mongodb://localhost:27017/food_inventory', { useNewUrlParser: true, useUnifiedTopology: true });

const foodSchema = new mongoose.Schema({
  name: String,
  category: String,
  quantity: Number,
  expirationDate: Date,
  price: Number
});

const Food = mongoose.model('Food', foodSchema);

//para tratamento de erros
const asyncHandler = fn => (req, res, next) => {
  Promise.resolve(fn(req, res, next)).catch(next);
};

//01 - listar todos os alimentos (GET)
app.get('/api/foods', asyncHandler(async (req, res) => {
  const foods = await Food.find();
  res.json(foods);
}));

//02 - buscar um alimento específico (GET)
app.get('/api/foods/:id', asyncHandler(async (req, res) => {
  const food = await Food.findById(req.params.id);
  if (!food) return res.status(404).json({message: 'Alimento não encontrado!'});
  res.json(food);
}));

//03 - criar um novo alimento (POST)
app.post('/api/foods', asyncHandler(async (req, res) => {
  const {name, category, quantity, expirationDate, price} = req.body;
  const food = new Food({name, category, quantity, expirationDate, price});
  const newFood = await food.save();
  res.status(201).json(newFood);
}));

//04 - atualizar um alimento existente (PUT)
app.put('/api/foods/:id', asyncHandler(async (req, res) => {
  const updatedFood = await Food.findByIdAndUpdate(req.params.id, req.body, {new: true, runValidators: true});
  if (!updatedFood) return res.status(404).json({message: 'Alimento não encontrado!'});
  res.json(updatedFood);
}));

// Rota para excluir um alimento pelo ID
app.delete('/api/foods/:id', asyncHandler(async (req, res) => {
  const food = await Food.findByIdAndDelete(req.params.id);
  if (!food) return res.status(404).json({message: 'Alimento não encontrado!'});
  res.json({message: 'Food deleted successfully'});
}));

//middleware de tratamento de erros
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).json({ message: err.message });
});

app.listen(port, () => {
  console.log(`Server is running on http://localhost:${port}`);
});
