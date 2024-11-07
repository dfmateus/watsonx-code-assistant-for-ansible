# IBM® watsonx™ Code Assistant(WCA) for Red Hat® Ansible Lightspeed

IBM® watsonx™ Code Assistant(WCA) for Red Hat® Ansible Lightspeed demystifies the process of Ansible Playbook creation through generative AI-powered content recommendations. This repository contains sample end-to-end demos, guidelines for best prompting practices, and guidelines for model customization.

<img src="https://github.com/user-attachments/assets/4b415ea3-a605-4cd7-896e-ccb3eb9743c1" width="150" align="left" alt="ANSIBLE_LIGHTSPED_ICON_SVG">

## Table of contents

<!--ts-->
* [**IBM® watsonx™ Code Assistant(WCA) for Red Hat® Ansible Lightspeed**](#table-of-contents)
  * [**Ansible Lightspeed Prompting Guide - Practical hands-on**](#)
  * [**Questions, Bug(Issue) or New Features(Contribute)**](#question-bugissuebug-or-new-featurescontribute-️)
  * [**License**](#-license-)
  * [**Copyright**](#copyright)
<!--te-->

---

## **Ansible Lightspeed Prompting Guide - Practical hands-on**

<img src="https://github.com/user-attachments/assets/d44d99e9-8d0b-42f8-a0af-639145e79839" width="300" align="left" alt="prompt-guide-8">
  
▶️ _A code editor extension that captures and transmits prompt and context information for inference and captures feed-back from the user to improve model and service quality._

▶️ _An inference pipeline for combining and processing natural language and Ansible-YAML to get code suggestions from a Large Language Models (LLMs)._

▶️ _A content matching pipeline that finds training examples that are similar to the code suggestions._

▶️ _An analysis framework that collects and processes feedback data to make it consumable by a wide range of analysis tools, ultimately for the purpose of improving model quality and user experience._

One of the key advantages of Ansible Lightspeed is its ability to leverage **context** and industry **best practices** to generate intelligent suggestions. As you use Ansible Lightspeed, you'll notice that it incorporates context from the overall Playbook and the specific task to provide more accurate recommendations. It analyzes the code you have already written and suggests improvements or additions based on established best practices.

---

<details>
  <summary>Here are some few examples for your reference</summary>

  <details>
    <summary>1. The clearer your Ansible task description, the better the inline prompt suggestions.</summary>

    ```yaml
    - name: Ensure the RPM package [yum-utils] is installed on RHEL Linux servers
      # Content suggestion provided by Ansible Lightspeed
      when: ansible_os_family == "RedHat"
      ansible.builtin.package:
        name: yum-utils
        state: present

    - name: Execute command needs-restarting -r to check if reboot is required
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.command: needs-restarting -r
      register: reboot_required_result
      changed_when: false
      failed_when: false
    ```

  </details> <!-- End of nested collapsible section 1 -->

  <details>
    <summary>2. Provide as much detail as possible in the task description, especially when copying/moving source and destination locations.</summary>

    ```yaml
    - name: Copy chroot_tasks.j2 to dest as chroot_tasks.sh on remote host(s)
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.template:
        src: chroot_tasks.j2
        dest: /tmp/chroot_tasks.sh
        mode: '0755'
        owner: root
        group: root
    ```

  </details> <!-- End of nested collapsible section 2 -->

  <details>
    <summary>3. If you require an item to be present at its destination, you essentially need to command its placement there.</summary>

    ```yaml
    - name: Ensure /var/tmp/ansible is in place
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.file:
        path: /var/tmp/ansible
        state: directory
        mode: '0755'
    ```

  </details> <!-- End of nested collapsible section 3 -->

  <details>
    <summary>4. If the suggestions or prompts don't return with the desired variable name, you can accept the suggestions and subsequently modify the variable name as usual.</summary>

    ```yaml
    - name: Copy httpd.conf.j2 template to /etc/httpd/conf/
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.template:
        src: httpd.conf.j2
        dest: /etc/httpd/conf/httpd.conf
        mode: '0644'
        owner: root
        group: root
    ```

  </details> <!-- End of nested collapsible section 4 -->

  <details>
    <summary>5. Take the opportunity to create tasks with register data that was generated in the previous task.</summary>

    ```yaml
    - name: "Get subscription status - Check if the system is already registered"
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.command: subscription-manager status
      register: subscription_status
      changed_when: false
      failed_when: false
    ```

  </details> <!-- End of nested collapsible section 5 -->

  <details>
    <summary>6. Ensure that if you require variables to be populated with values from previously filled variables, you declare this in the vars file and specify it in the Task description field.</summary>

    ```yaml
    vars:
        oscap_rhel_pkgs:
          - openscap
          - openscap-scanner
          - openscap-utils
          - scap-security-guide
          - mailx

    - name: Ensure OpenSCAP RPM Packages are installed for {{ oscap_rhel_pkgs }}
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.package:
        name: "{{ oscap_rhel_pkgs }}"
        state: present
    ```

  </details> <!-- End of nested collapsible section 6 -->

  <details>
    <summary>7. To automatically fill a service or content with a value from a variable, specify this requirement clearly in the task description.</summary>

    ```yaml
    vars:
        welcome_note: "Welcome to Demo Web Server"

    - name: Create new file /var/www/html/index.html with content of var welcome_note
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.copy:
        content: "{{ welcome_note }}"
        dest: /var/www/html/index.html
    ```

  </details> <!-- End of nested collapsible section 7 -->

  <details>
    <summary>8. Ensure that clear and objective specifications are provided, especially when certain conditions must be met for a task to be completed, as commonly utilized in the `when:` condition.</summary>

    ```yaml
    - name: Inserts/replaces the openat rule in /etc/audit/audit.rules when on x86_64
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.lineinfile:
        path: /etc/audit/audit.rules
        regexp: '^.*openat.*'
        line: '-a always,exit -F arch=b64 -S openat'
        state: present
      when: ansible_architecture == "x86_64"
    ```

  </details> <!-- End of nested collapsible section 8 -->

  <details>
    <summary>9. If any inline suggestions don't come up with the variable name you want, instead of accepting it and then changing the name of that variable, you can try changing the task name, there are several synonyms or alternative phrases that you can use it.</summary>

    ```yaml
    - name: Print the upgrade_inhibited var
      ansible.builtin.debug:
        msg: "{{ _msg_ }}"
    ```

  </details> <!-- End of nested collapsible section 9 -->

  <details>
    <summary>10. If you want to use values in a variable, you can call it in a few ways calling `{{ <VARIABLE_NAME> }}`, `var`, `variable` and so on...</summary>

    ```yaml
    - name: Start and enable {{ wordpress_app }} services
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.service:
        name: "{{ item }}"
        state: started
        enabled: true
      loop:
        - "{{ wordpress_app }}"
    ```

  </details> <!-- End of nested collapsible section 10 -->

</details> <!-- End of top-level collapsible section -->

---

**11.** Previously highlighted, generative AI demonstrates robust contextual understanding. Consequently, when addressing specific tasks or activities, the AI adeptly maintains and adheres to established contextual parameters.  

<details>
  <summary>Click here to check few examples for your reference ⬇️</summary>

  ```yaml
  - name: Check if /var/lib/pgsql/data exists
    # Content suggestion provided by Ansible Lightspeed
    ansible.builtin.stat:
      path: /var/lib/pgsql/data
    register: var_lib_pgsql_data

  - name: End play if /var/lib/psql/data does not exist
    # Content suggestion provided by Ansible Lightspeed
    ansible.builtin.meta: end_play
    when: not var_lib_pgsql_data.stat.exists

  - name: Take a Backup of file /var/lib/pgsql/data
    # Content suggestion provided by Ansible Lightspeed
    ansible.builtin.copy:
      src: /var/lib/pgsql/data
      dest: /var/lib/pgsql/data.bak
      remote_src: true

  - name: Remove the file /var/lib/pgsql/data after backup
    # Content suggestion provided by Ansible Lightspeed
    ansible.builtin.file:
      path: /var/lib/pgsql/data
      state: absent

  - name: Get all mountpoints with noexec option
    # Content suggestion provided by Ansible Lightspeed
    ansible.builtin.shell: mount | grep noexec
    register: mountpoints

  - name: Remount noexec partitions with exec option if it's found any
    # Content suggestion provided by Ansible Lightspeed
    ansible.posix.mount:
      path: "{{ item }}"
      state: remounted
      src: "{{ item }}"
      fstype: "{{ item }}"p
      opts: exec
    when: mountpoints.stdout | length > 0
    loop: "{{ mountpoints.stdout_lines |flatten(levels=1) }}"
  ```
</details>

**12.** If you require the execution of any module or command by the Ansible Controller node, ensure a clear and explicit specification  

<details>
  <summary>Click here to check few examples for your reference ⬇️</summary>

  ```yaml
  - name: Send an e-mail with oficial module using the Ansible controller node without superuser
    # Content suggestion provided by Ansible Lightspeed
    delegate_to: localhost
    community.general.mail:
      host: localhost
      port: 25
      subject: Ansible mail
      to: root
      body: Ansible mail body
  ```
  ```yaml
  - name: Sending an e-mail only once using the Ansible delegate node {{ bastion_ip }} without superuser
    # Content suggestion provided by Ansible Lightspeed
    community.general.mail:
      host: localhost
      port: 25
      subject: Ansible mail test
      to: root
      from: oliver4@example.com
      body: Ansible mail test body
    delegate_to: "{{ bastion_ip }}"
    become: false
    run_once: true
  ```
</details>

**13.** if the prompting suggestions doesn't make sense the Regular expression to find, replace something you can teach the Watsonx Code Assistant to use your regular expression, into the requisite module requested.  

<details>
  <summary>Click here to check few examples for your reference ⬇️</summary>

  ```yaml
  - name: Find /etc/audit/ file(s) matching ^audit(\.rules|d\.conf)$
    # Content suggestion provided by Ansible Lightspeed
    ansible.builtin.find:
      paths: /etc/audit/
      patterns: audit(\.rules|d\.conf)$
    register: audit_files
  ```
  or
  ```yaml
  - name: Replace in the /etc/fstab file that matches (.*)cifs(.*)
    # Content suggestion provided by Ansible Lightspeed
    ansible.builtin.replace:
      path: /etc/fstab
      regexp: ^(.*)cifs(.*)
      replace: '#\1cifs\2'
  ```
</details>

<img src="https://github.com/user-attachments/assets/6ac1505e-ac0a-4cf8-bf8f-74cb78a4e9ca" width="300" align="left" alt="prompt-guide-10">

**_Here are my final advice for you do not hesitate to utilize extensive prompts; in certain scenarios, this approach can enhance the accuracy of prompt suggestions generated by the AI. In summary, a well-crafted prompt is crucial for optimal outcomes._**

---

## **_Question❓, Bug(issue):bug: or New Features(Contribute)_** 🙋‍♂️

<!-- Questions can be useful but optional, this gives you a place to say, "This is how to contact this project maintainers or create PRs -->
If you have any questions, issues or feature requests you can create a new issue [**> Click Here <**](https://github.com/IBM/watsonx-code-assistant-for-ansible/issues/)

---

## 📝 **_License_** 📝

[Apache License 2.0](http://www.apache.org/licenses/)

---

## **_Copyright_**

©️ Copyright IBM Corporation 2024