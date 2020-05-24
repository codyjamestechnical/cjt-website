---
title: Contact
date: 2020-05-24T02:48:58.000+00:00
menu:
  main:
    weight: 5

---
{{< script >}}
  window.onload = function() {
  var recaptcha = document.forms["contact"]["g-recaptcha-response"];
  recaptcha.required = true;
  recaptcha.oninvalid = function(e) {
    // do something
    alert("Please complete the captcha");
  }
}
{{< /script >}}
<link rel="stylesheet" href="https://themes.gohugo.io//theme/LoveIt/lib/valine/valine.min.css">
<link rel="stylesheet" href="https://codyjames.dev/uploads/CSS.css">
<form name="contact" method="POST" netlify-honeypot="how many bugs" data-netlify-recaptcha="true" data-netlify="true">
<div id="valine" class="comment v" data-class="v">
<div class="vpanel">
<div class="vwrap">


  <input name="how many bugs" hidden placeholder="How Many Bugs?" />
	<div class="vheader item3">
    <input class="vinput" type="text" name="name" placeholder="Name" required />  
    <input class="vinput" type="email" name="email" placeholder="E-Mail" required />
    <select class="vinput vselect" name="reason[]" required>
      <option value="" disabled selected hidden>Reason for Contacting</option>
      <option value="Computer_Repair">Computer Repair</option>
      <option value="Website_Dev">Website Development</option>
      <option value="Coding">Application Development</option>
      <option value="Tech_Consult">General Tech Consultation</option>
      <option value="Networking">Home Network Setup and Repair</option>
      <option value="Other">Other</option>
    </select>
    </div>
    
 <div class="vedit">
    <textarea class="veditor vinput" required name="message" placeholder="Message..."></textarea>
  </div>
  <div class="vrow">
  <div  class="vcol vcol-30">

  </div>
  	<div class="vcol vcol-70 text-right">
  	<button class="vsubmit vbtn" type="submit">Send Message</button>
  	</div>
  	</div>

</div>
</div>
</div>
<div data-netlify-recaptcha="true" class="recaptcha"></div>
</form>