# CodeAlpha_Code Review task



vulnerable_app/ - intentionally vulnerable Flask app 
secure_app/ - remediated version
reports/ the audit report
Run the scans
pip install bandit semgrep pip-audit
bandit -r vulnerable_app -f txt -o reports/bandit_vulnerable.txt
bandit -r secure_app -f txt -o reports/bandit_secure.txt
semgrep --config p/python --config p/flask vulnerable_app
Run the app
cd vulnerable_app && pip install -r requirements.txt && python app.py

cd secure_app && pip install -r requirements.txt
export SECRET_KEY=$(python -c 'import secrets; print(secrets.token_hex(32))') COOKIE_SECURE=0
python app.py
