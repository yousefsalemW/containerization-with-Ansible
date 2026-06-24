# Containerization with Ansible

أتمتة تثبيت Docker ونشر موقع ويب كـ container على بيئة Linux مختلطة (Rocky + Ubuntu) باستخدام Ansible.

## نظرة عامة

المشروع بيستخدم Ansible roles لـ:

1. تثبيت Docker CE الرسمي على كل الـ hosts، مع التعامل التلقائي مع اختلاف التوزيعات.
2. نشر موقع ويب داخل container من image مخصصة على كل الماشينات.

## التشغيل

\`\`\`bash
# تثبيت Docker على كل ال Machines 
ansible-playbook install-docker.yml

# نشر الموقع
ansible-playbook deploy-webapp.yml
\`\`\`

بعد التشغيل، الموقع بيكون متاح على البورت 8080 على كل Machines .

## البيئة

- Control node: manager
- Managed hosts: rocky (Rocky Linux), ubuntu, test (Ubuntu)
- Image: alnaqib/efe-egy-web (Apache httpd 2.4)
