# Copilot / Claude Quiz Prompts

> Copy a prompt, paste into Claude / Copilot / Gemini / ChatGPT for self-quiz.

<style>
.q-card{border:1px solid #2a3960;border-radius:10px;padding:14px 16px;margin:12px 0;background:#0e1733;}
.q-card h3{margin:0 0 6px;font-size:1.05rem;}
.q-card .row{display:flex;gap:8px;flex-wrap:wrap;margin-top:8px;}
.q-card button{padding:6px 10px;border-radius:6px;border:1px solid #355;background:#142244;color:#cfe;cursor:pointer;}
.q-card button:hover{background:#1d2d59;}
</style>

<div class="q-card" data-prompt="Quiz me on Claude model tiers: 5 multiple-choice questions on when to use Haiku vs Sonnet vs Opus. Give answers and short rationale at the end.">
<h3>1. Model tier selection</h3>
<p>5 MCQs on Haiku vs Sonnet vs Opus selection criteria.</p>
<div class="row"><button class="copy">Copy</button><button class="open" data-target="claude">Open Claude</button><button class="open" data-target="copilot">Open Copilot</button><button class="open" data-target="chatgpt">Open ChatGPT</button><button class="open" data-target="gemini">Open Gemini</button></div>
</div>

<div class="q-card" data-prompt="Generate 5 scenario questions about prompt engineering for Claude using the RTCEF framework. For each: scenario, question, 4 options, correct answer, why.">
<h3>2. Prompt design scenarios</h3>
<p>5 scenario questions on RTCEF, XML tags, long context.</p>
<div class="row"><button class="copy">Copy</button><button class="open" data-target="claude">Open Claude</button><button class="open" data-target="copilot">Open Copilot</button><button class="open" data-target="chatgpt">Open ChatGPT</button><button class="open" data-target="gemini">Open Gemini</button></div>
</div>

<div class="q-card" data-prompt="Ask me 5 questions about Claude tool use: defining tools, parsing tool_use blocks, returning tool_result, agent loop termination, prompt-injection from tool outputs. Wait for my answer before revealing the next question.">
<h3>3. Tool use and agents</h3>
<p>5 interactive questions on tool use loop and safety.</p>
<div class="row"><button class="copy">Copy</button><button class="open" data-target="claude">Open Claude</button><button class="open" data-target="copilot">Open Copilot</button><button class="open" data-target="chatgpt">Open ChatGPT</button><button class="open" data-target="gemini">Open Gemini</button></div>
</div>

<div class="q-card" data-prompt="Quiz me on Claude production ops: prompt caching, Batches API, model pinning, evaluation, PII handling, retries. 6 questions, mix MCQ and short answer.">
<h3>4. Production operations</h3>
<p>6 mixed questions on caching, batches, evaluation, ops.</p>
<div class="row"><button class="copy">Copy</button><button class="open" data-target="claude">Open Claude</button><button class="open" data-target="copilot">Open Copilot</button><button class="open" data-target="chatgpt">Open ChatGPT</button><button class="open" data-target="gemini">Open Gemini</button></div>
</div>

<script>
const TARGETS = {
  claude:   'https://claude.ai/new',
  copilot:  'https://copilot.microsoft.com/',
  gemini:   'https://gemini.google.com/app',
  chatgpt:  'https://chat.openai.com/',
};
document.querySelectorAll('.q-card').forEach(card => {
  const prompt = card.getAttribute('data-prompt') || '';
  card.querySelector('.copy')?.addEventListener('click', async () => {
    try { await navigator.clipboard.writeText(prompt); }
    catch (e) { const ta = document.createElement('textarea'); ta.value = prompt; document.body.appendChild(ta); ta.select(); document.execCommand('copy'); ta.remove(); }
    const b = card.querySelector('.copy'); const t = b.textContent; b.textContent = 'Copied!'; setTimeout(()=>b.textContent=t,1200);
  });
  card.querySelectorAll('.open').forEach(btn => {
    btn.addEventListener('click', async () => {
      try { await navigator.clipboard.writeText(prompt); } catch(e) {}
      const url = TARGETS[btn.getAttribute('data-target')];
      if (url) window.open(url, '_blank', 'noopener');
    });
  });
});
</script>
