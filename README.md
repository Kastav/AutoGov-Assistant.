function generate() {
  let name = document.getElementById("name").value;
  let age = parseInt(document.getElementById("age").value);
  let state = document.getElementById("state").value;

  let output = `<h3>Hello ${name} 👋</h3>`;
  output += `<p>State: ${state}</p>`;

  let checklist = [];

  if (age >= 18) {
    output += `<p>✅ You are eligible for:</p>
    <ul>
      <li>PAN Card - https://www.onlineservices.nsdl.com</li>
      <li>Voter ID - https://voters.eci.gov.in</li>
      <li>Bank Account</li>
    </ul>`;

    output += `<p>🧠 AI Insight: At your age, financial identity and voting rights become important.</p>`;

    checklist.push("PAN Card", "Voter ID", "Bank Account");

    if (state.toLowerCase() === "chhattisgarh") {
      output += `<p>🎯 Check Chhattisgarh state schemes.</p>`;
    }

  } else if (age >= 16) {
    output += `<p>⚡ You can apply for:</p>
    <ul>
      <li>Learning Driving License</li>
    </ul>`;
    checklist.push("Learning License");

  } else {
    output += `<p>📌 No major documents required yet.</p>`;
    let yearsLeft = 18 - age;
    output += `<p>⏳ You will be eligible in ${yearsLeft} years.</p>`;
  }

  // Checklist
  if (checklist.length > 0) {
    output += `<h4>📋 Checklist:</h4>`;
    checklist.forEach(item => {
      output += `<input type="checkbox"> ${item}<br>`;
    });
  }

  // Suggestions
  output += `<h4>🚀 Next Steps:</h4>
  <ul>
    <li>Build financial identity</li>
    <li>Secure documents digitally</li>
    <li>Stay updated with government schemes</li>
  </ul>`;

  // Government platforms
  output += `<h4>Useful Platforms:</h4>
  <ul>
    <li>DigiLocker</li>
    <li>Aadhaar Services</li>
  </ul>`;

  document.getElementById("output").innerHTML = output;
}

// AI button
function askAI() {
  let age = document.getElementById("age").value;
  let query = "What government documents should a " + age + " year old Indian apply for?";
  let url = "https://www.perplexity.ai/search?q=" + encodeURIComponent(query);
  window.open(url, "_blank");
}
