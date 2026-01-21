## exposing frappe site with ngrok
```
cd frappe-bench/
bench pip install pyngrok
bench --site [site_name] set-config ngrok_authtoken your_ngrok_authtoken
bench --site [site_name] set-config http_port 8000
bench start
bench --site [site_name] ngrok --bind-tls
```
