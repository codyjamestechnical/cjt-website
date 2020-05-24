---
title: "Contact"
date: 2020-05-23T22:48:58-04:00
draft: false
---

<form name="contact" method="POST" data-netlify="true">
  <p>
    <label>Your Name: <input type="text" name="name" /></label>   
  </p>
  <p>
    <label>Your Email: <input type="email" name="email" /></label>
  </p>
  <p>
    <label>Your Reson for Contacting Me: <select name="reason[]" multiple>
      <option value="Computer_Repair">Computer Repair</option>
      <option value="Website_Dev">Website Development</option>
      <option value="Coding">Application Development</option>
      <option value="Tech_Consult">General Tech Consultation</option>
      <option value="Networking">Home Network Setup & Repair</option>
      <option value="Other">Other</option>
    </select></label>
  </p>
  <p>
    <label>Message: <textarea name="message"></textarea></label>
  </p>
  <p>
    <button type="submit">Send</button>
  </p>
</form>
