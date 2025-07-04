const express = require('express');
const mongoose = require('mongoose');
const cors = require('cors');
const taskRoutes = require('./routes/taskRoutes');

const app = express();
app.use(cors());
app.use(express.json());

mongoose.connect('mongodb://localhost:27017/taskdb', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
}).then(() => console.log("MongoDB Connected"))
  .catch(err => console.log(err));

app.use('/api/tasks', taskRoutes);

app.listen(5000, () => console.log("Server running on port 5000"));
