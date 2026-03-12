const KEY = ['gsk_QIDhbhOIdp0kx2rc','5oGMWGdyb3FYIesX2g1y','ksAskkV5M06U2Eo0'].join('');

export default async function handler(req, res) {
  res.setHeader('Access-Control-Allow-Origin', '*');
  res.setHeader('Access-Control-Allow-Methods', 'POST, OPTIONS');
  res.setHeader('Access-Control-Allow-Headers', 'Content-Type');

  if (req.method === 'OPTIONS') return res.status(200).end();
  if (req.method !== 'POST') return res.status(405).json({error:'Method not allowed'});

  try {
    const body = typeof req.body === 'string' ? JSON.parse(req.body) : req.body;
    const groqRes = await fetch('https://api.groq.com/openai/v1/chat/completions', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'Authorization': 'Bearer ' + KEY
      },
      body: JSON.stringify(body)
    });
    const data = await groqRes.json();
    return res.status(groqRes.status).json(data);
  } catch(e) {
    return res.status(500).json({error:{message: e.message}});
  }
}
