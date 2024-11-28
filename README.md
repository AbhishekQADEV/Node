## Developer Certificate of Origin and License
By contributing to GitLab B.V., you accept and agree to the following terms and conditions for your present and future contributions submitted to GitLab B.V. Except for the license granted herein to GitLab B.V. and recipients of software distributed by GitLab B.V., you reserve all right, title, and interest in and to your Contributions. All contributions are subject to the Developer Certificate of Origin and license set out at [docs.gitlab.com/ce/legal/developer_certificate_of_origin](https://docs.gitlab.com/ce/legal/developer_certificate_of_origin). _This notice should stay as the first item in the CONTRIBUTING.md file._
## Code of conduct
As contributors and maintainers of this project, we pledge to respect all people who contribute through reporting issues, posting feature requests, updating documentation, submitting pull requests or patches, and other activities. We are committed to making participation in this project a harassment-free experience for everyone, regardless of level of experience, gender, gender identity and expression, sexual orientation, disability, personal appearance, body size, race, ethnicity, age, or religion. Examples of unacceptable behavior by participants include the use of sexual language or imagery, derogatory comments or personal attacks, trolling, public or private harassment, insults, or other unprofessional conduct.
Project maintainers have the right and responsibility to remove, edit, or reject comments, commits, code, wiki edits, issues, and other contributions that are not aligned to this Code of Conduct. Project maintainers who do not follow the Code of Conduct may be removed from the project team. This code of conduct applies both within project spaces and in public spaces when an individual is representing the project or its community. Instances of abusive, harassing, or otherwise unacceptable behavior can be reported by emailing contact@gitlab.com. This Code of Conduct is adapted from the [Contributor Covenant](https://contributor-covenant.org), version 1.1.0, available at [https://contributor-covenant.org/version/1/1/0/](https://contributor-covenant.org/version/1/1/0/).
FROM node:21-alpine 
WORKDIR /usr/src/app
COPY . .
RUN npm install
EXPOSE 80
CMD [ "npm", "start" ]
MIT License
Copyright(c)2017-Present GitLab B.V.
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files(the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions: The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

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

{
    "name": "demo",
    "version": "0.0.0",
    "lockfileVersion": 3,
    "requires": true,
    "packages": {
        "": {
            "name": "demo",
            "version": "0.0.0",
            "license": "MIT",
            "dependencies": {
                "express": "^4.18.2"
            },
            "devDependencies": {
                "mocha": "^10.2.0",
                "supertest": "^6.3.4"
            }
        }
    }
}