<script>
  const startBtn = document.getElementById('start');
  const resultDiv = document.getElementById('result');
  const resMsg = document.getElementById('resMsg');
  const extra = document.getElementById('extra');
  const bar = document.getElementById('bar');
  const captchaInput = document.getElementById('captcha');
  const verifyBtn = document.getElementById('verify');

  verifyBtn.onclick = () => {
    if(captchaInput.value.trim().toLowerCase() === 'ben robot değilim'){
      verifyBtn.innerText = 'Doğrulandı ✓';
      verifyBtn.disabled = true;
    } else {
      alert('Lütfen doğru CAPTCHA\'yı yaz (Ben robot değilim)');
    }
  };

  startBtn.onclick = () => {
    if(!verifyBtn.disabled){
      alert('Lütfen önce CAPTCHA\'yı doğrula!');
      return;
    }

    const user = document.getElementById('username').value.trim() || 'Kullanıcı';
    const amount = document.getElementById('amount').value;

    resultDiv.style.display = 'block';
    resMsg.innerText = 'Robux oluşturuluyor...';
    extra.innerText = 'Sunucuya bağlanılıyor (simüle)...';
    bar.style.width = '0%';

    let progress = 0;
    const interval = setInterval(() => {
      progress += 10;
      bar.style.width = progress + '%';

      if(progress >= 100){
        clearInterval(interval);
        resMsg.innerText = `${user} kullanıcısına ${amount} Robux verildi!`;
        extra.innerText = 'Şaka! Bu sadece bir prank, gerçek değil 😅';
        verifyBtn.disabled = false;
        verifyBtn.innerText = 'Doğrula';
        captchaInput.value = '';
      }
    }, 300);
  };
</script>
