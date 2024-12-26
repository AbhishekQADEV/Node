const axios = require('axios');
const fs = require('fs');
const path = require('path');

const urls = [
  'https://jsonplaceholder.typicode.com/posts',
  'https://jsonplaceholder.typicode.com/comments',
  'https://jsonplaceholder.typicode.com/albums',
  'https://jsonplaceholder.typicode.com/photos',
  'https://jsonplaceholder.typicode.com/todos',
  'https://jsonplaceholder.typicode.com/users'
];

// Parallelize the asynchronous operations using Promise.all
Promise.all(urls.map(url => axios.get(url)))
  .then(responses => {
    const data = responses.map(response => response.data);
    const jsonData = JSON.stringify(data);

    // Write the JSON data to a file
    fs.writeFile(path.join(__dirname, 'data.json'), jsonData, err => {
      if (err) {
        console.error('Error writing data to file:', err);
      } else {
        console.log('Data written to file successfully');
      }
    });
  })
  .catch(error => {
    console.error('Error fetching data:', error);
  });