# Socket.io with React

---

## server-side (Express)

```javascript
const express = require('express');
const socket = require('socket.io');
const cors = require('cors');

const app = express();

app.use(cors());

const server = app.listen(process.env.PORT || 5000, () => {
  console.log('Listening on 5000 ...')
})
const io = socket(server);

io.on('connection', socket => {
  console.log('made socket connection')
})
```

## client-side (React)

```javascript
import io from 'socket.io-client'

componentDidMount() {
  const socket = io('http://127.0.0.1:5000');
  socket.on('connect', () => {
    console.log('Connected!')
  })
  this.setState({
    socket
  })
}
```

