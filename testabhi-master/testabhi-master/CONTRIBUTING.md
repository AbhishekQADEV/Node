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

// Function to write data to file
const writeDataToFile = (data) => {
  const jsonData = JSON.stringify(data);
  fs.writeFile(path.join(__dirname, 'data.json'), jsonData, err => {
    if (err) {
      console.error('Error writing data to file:', err);
    } else {
      console.log('Data written to file successfully');
    }
  });
};

// Function to fetch data from URLs
const fetchData = async (url) => {
  try {
    const response = await axios.get(url);
    return response.data;
  } catch (error) {
    console.error('Error fetching data:', error);
    return null;
  }
};

// Function to fetch data from all URLs in parallel
const fetchAllData = async (urls) => {
  try {
    const responses = await Promise.all(urls.map(url => fetchData(url)));
    const data = responses.filter(response => response !== null);
    return data;
  } catch (error) {
    console.error('Error fetching data:', error);
    return null;
  }
};

// Main function to fetch and write data to file
const main = async () => {
  const data = await fetchAllData(urls);
  if (data !== null) {
    writeDataToFile(data);
  }
};

// Call the main function
main();