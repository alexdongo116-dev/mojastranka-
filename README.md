// mobile menu toggle
  document.getElementById('burgerBtn').addEventListener('click', function(){
    document.querySelector('.nav-links').style.display =
      document.querySelector('.nav-links').style.display === 'flex' ? 'none' : 'flex';
  });

  // faq accordion
  document.querySelectorAll('.faq-item button').forEach(function(btn){
    btn.addEventListener('click', function(){
      var expanded = btn.getAttribute('aria-expanded') === 'true';
      document.querySelectorAll('.faq-item button').forEach(function(b){ b.setAttribute('aria-expanded','false'); b.parentElement.classList.remove('open-faq'); b.nextElementSibling.style.display='none'; });
      if(!expanded){
        btn.setAttribute('aria-expanded','true');
        btn.nextElementSibling.style.display='block';
      }
    });
    btn.nextElementSibling.style.display='none';
  });

  // simple site search: jumps to and highlights matching section by keyword
  var searchMap = {
    'obrubník': '#sluzby', 'obrubniky':'#sluzby', 'dlažb':'#sluzby', 'dlazb':'#sluzby',
    'asfalt':'#sluzby', 'odvod':'#sluzby', 'proces':'#proces', 'postup':'#proces',
    'referen':'#referencie', 'galéria':'#referencie', 'recenz':'#recenzie',
    'otázk':'#faq', 'faq':'#faq', 'kontakt':'#kontakt', 'cena':'#kontakt', 'ponuk':'#kontakt'
  };
  document.getElementById('siteSearch').addEventListener('keydown', function(e){
    if(e.key === 'Enter'){
      var q = e.target.value.trim().toLowerCase();
      var target = null;
      Object.keys(searchMap).forEach(function(key){
        if(q.indexOf(key) !== -1) target = searchMap[key];
      });
      if(target){ document.querySelector(target).scrollIntoView({behavior:'smooth'}); }
    }
  });

  // contact form (demo only — no backend)
  document.getElementById('contactForm').addEventListener('submit', function(e){
    e.preventDefault();
    document.getElementById('formNote').style.display = 'block';
    e.target.reset();
  });
