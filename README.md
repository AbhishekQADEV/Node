const express = require('express');
const request = require('supertest');
const assert = require('assert');

const app = express();
const port = process.env.PORT || 5000;

app.get('/', (req, res) => {
    return res.status(200).send({
        message: "Hello World!"
    });
});

app.listen(port, () => {
    console.log("Listening on " + port);
});

describe('GET /', () => {
    it('responds responds to the world', async function() {
        const res = await request(app).get('/').set('Accept', 'application/json');
        assert.equal(res.status, 200);
        assert.equal(res.type, 'application/json');
        assert.equal(res.body.message, 'Hello World!');
    });
});

describe('GET /404', () => {
    it('responds with a 404', async function() {
        const res = await request(app).get('/404').set('Accept', 'application/json');
        assert.equal(res.status, 404);
    });
});

module.exports = app;