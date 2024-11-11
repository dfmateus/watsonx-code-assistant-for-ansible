# _IBM® watsonx™ Code Assistant for Ansible Lightspeed_

<img src="https://github.com/user-attachments/assets/4b415ea3-a605-4cd7-896e-ccb3eb9743c1" width="120" align="left" alt="ANSIBLE_LIGHTSPED_ICON_SVG">

_**IBM® watsonx™ Code Assistant(WCA) for Red Hat® Ansible Lightspeed** demystifies the process of Ansible Playbook creation through generative AI-powered content recommendations. This repository contains sample end-to-end demos, guidelines for best prompting practices, and guidelines for model customization._

## Table of Contents

- [Introduction](#table-of-contents)
- [Key feature: Single-Task Generation](#key-feature-single-task-generation)
  - [DEMO: Single-Task Generation](#demo---single-task-generation)
- [Key feature: Multi-Task Generation](#key-feature-multi-task-generation)
  - [DEMO: Multi-Task Generation](#demo---multi-task-generation)
- [Key feature: Playbook Generation](#key-feature-playbook-generation)
  - [DEMO: Playbook Generation](#demo---full-playbook-generation)
- [Key feature: Playbook Explanation](#key-feature-playbook-explanation)
- [Key feature: Model Customization](#key-feature-model-customization)
- [Ansible Lightspeed Prompting Guide - Practical hands-on](#ansible-lightspeed-prompting-guide---practical-hands-on)
- [Questions, Bug(Issue) or New Features(Contribute)](#question-bugissue--or-new-featurescontribute-️)
- [License](#-license-)
- [Copyright](#copyright)

---
## **Key feature: Single-Task Generation** 

<img src="https://github.com/user-attachments/assets/2346bd2f-db2b-4587-b2d5-6a5dbab37687" width="120" align="left" alt="single-task-png">

_IBM® watsonx™ Code Assistant for Ansible Lightspeed offers a chat-style experience that allows users to generate and explain Ansible content from single task prompts. This tool collects user prompts and returns an outline of an Ansible playbook, simplifying the process of creating and understanding Ansible content._

🚀 _**Take a look at the example GIF below to see it in action!**_ 🚀

```yaml
---
- name: Configure Database servers
  hosts: databases
  become: true

  tasks:
    - name: Install postgresql-server
```

- Move your cursor to the end of the **`- name: Install postgresql-server`** task description.
- Press **"ENTER"** to generate a suggestion.
- Press **"TAB"** to accept 👍 the suggestion.

<img src="https://github.com/user-attachments/assets/f03de63b-5f23-418d-babf-2c3d93a439d4" alt="single-task-gif">

## **DEMO - Single-Task Generation**
👉 Click [**here**](./demos/single-task/) to explore the demonstrations and get hands-on experience in real-world scenarios.

---

## **Key feature: Multi-Task Generation** 

<img src="https://github.com/user-attachments/assets/adf2b4da-8d59-47d6-bfb3-3998c0b77de5" width="120" align="left" alt="multi-task-png">

_IBM® watsonx™ Code Assistant for Ansible Lightspeed offers a chat-style experience that allows users to generate multiple tasks with a single prompt entry, by chaining multiple tasks descriptions using ampersand **(&)** sign in a YAML comment at the task level._

🚀 _**Take a look at the example GIF below to see it in action!**_ 🚀

- Move your cursor to the end of the line 
  
```yaml
# Run postresql-setup command & Start and enable postgresql service & Allow the traffic
```

- Press **"ENTER"** to generate a suggestion with multiple.
- Press **"TAB"** to accept 👍 the suggestion.

<img src="https://github.com/user-attachments/assets/35a1e224-58fd-4fcd-a5e2-1fa51fdaed85" alt="multi-task-gif">

**Note:** _Generating contextually aware, accurate Ansible content suggestions saves you time and helps you create efficiently. One of Red Hat Ansible Lightspeed’s superpowers is **context.** The last task just asks to **"Allow the traffic"**, which might seem counterintuitive as an AI **"ask"**, but the Red Hat Ansible Lightspeed service is aware of the Ansible Playbook it's working in and suggests a port suggestion to open which corresponds to the default port for **PostgreSQL(5432).**_

## **DEMO - Multi-Task Generation**
👉 Click [**here**](./demos/multi-task/) to explore the demonstrations and get hands-on experience in real-world scenarios.

---

## **Key feature: Playbook Generation** 

<img src="https://github.com/user-attachments/assets/7d061158-6feb-4e24-b52b-057ca1326cda" width="120" align="left" alt="playbook-generation-png">

_Playbook generation is designed to overcome the challenges of generating Ansible content Playbooks from scratch. It leverages a chat-style experience that generates **Full Ansible Playbooks** from both **single** and **multi-task** prompts._  

_The new feature Playbook generation eases that burden by leveraging a chat-style and generative AI-powered user interface that allows users to write prompts using natural language to generate full Ansible Playbooks. Users simply input a prompt and the tool will generate a set of steps that will be needed in order to run the Playbook. Once accepted, watsonx Code Assistant for Red Hat Ansible Lightspeed will provide a **Full Ansible Playbook**._

🚀 _**Take a look at the example GIF below to see it in action!**_ 🚀

**How to access Playbook Generation?**  
Click on the **'Ansible'** icon on VS Code's Activity Bar  
Under **'Ansible Content Creator'** -> **'Get Started'**  
Under **'Create'** -> **'Playbook with Ansible Lightspeed'**

**🎯 Copy the content below and paste into the textarea.**
  
```yaml
Install and enable PostgreSQL
```

- Press **"Analyze"** to proceed.
- **Review the suggested steps for your playbook and modify as needed.** _(Prompt refinement)_
- Press **"Generate playbook"** to open a new tab file with the full playbook.

<img src="https://github.com/user-attachments/assets/0008a253-16f8-4597-ac8d-5c2c990ef45e" alt="playbook-generation-gif">

**Note:** _The feature exclusively creates **self-contained** Full Playbooks — it does not generate Ansible roles._

## **DEMO - Full Playbook Generation**
👉 Click [**here**](./demos/playbook-generation/) to explore the demonstrations and get hands-on experience in real-world scenarios.

---

### **Key feature: Playbook Explanation**

<img src="https://github.com/user-attachments/assets/c58ffb05-172a-4e15-92ed-a21c08a358e0" width="220" align="left" alt="playbook-explanation-png">

_Playbook explanation is designed to overcome the challenges of understanding complex Playbooks._  

_users can acquire explanations of each Playbook including a detailed summary of what the Playbook is doing, the perquisites for running the Playbook and a description of each task._

This ensures that each development team member — regardless of expertise — can understand each task and Playbook efficiently to help minimize the learning curve for faster automation content creation.

With Playbook explanation, developers can get AI-generated explanations with the click of a button. This includes a summary of the Playbook and a description of each task to better understand what the Playbook is doing. 

This especially helps to:

- **Reduce the knowledge gap:** with a chat-style experience and real-time explanation of Ansible content, developers without deep Ansible expertise can quickly learn what the code is doing to accelerate content creation or automation efforts  
- **Free up your senior subject matter experts:** for simpler Ansible content creation, developers can leverage the playbook generation feature to generate syntactically correct content recommendations faster. This allows them to focus their time on more complex work.  
- **Increase Ansible Playbook understanding:** explanation helps to understand new and existing Ansible Playbooks faster, saving developers time to focus on more critical tasks and accelerate their productivity for future maintainability.  

**How to access Playbook Explanation?**  
There are 2 ways you can initiate Playbook explanation:  
Right click on the **Playbook** -> **'Explain the playbook with Ansible Lightspeed'**  
Click on the **'Ansible'** icon on VS Code's Activity Bar -> Under **'Ansible Lightspeed'** -> **'Explain the current playbook'**  

<img src="https://github.com/user-attachments/assets/dff0b077-f7ec-4e95-a9dc-9dae174a8a45" alt="playbook-explanation-gif">  

❗ **NOTE:** ❗
- _You can run playbook explanation on any existing Ansible playbooks._ 
- _Playbook explanations are strictly limited to self-contained Full Playbooks—they do not cover task files or role files._

**Video by [Anshul Behl](https://www.linkedin.com/in/ianshulbehl/) Principal Technical Marketing Manager by Red Hat®** 👇  
🎥 [Playbook Generation using Ansible Lightspeed with IBM watsonx Code Assistant](https://youtu.be/oS7mSykl_D0?list=PLdu06OJoEf2bVLR899FuKc3AiuJvbIRZU)

**Video by [Ian Smalley](https://www.linkedin.com/in/ian-smalley-3932a21b/) Editor by IBM® Technology** 👇  
🎥 [Ansible Playbook Creation with IBM watsonx Code Assistant](https://youtu.be/vG54TKeEwP4)

---

### **Key feature: Model Customization** 

<img src="https://github.com/user-attachments/assets/3c940bed-0ed6-4afe-8380-aec5b2755642" width="120" align="left" alt="model-customization-png">

As a customer grows their Ansible Content library (or when IBM releases and updated base model), It makes sense to re-tune.

Since every organization is different, **watsonx Code Assistant for Red Hat Ansible Lightspeed** allows users to customize the AI model with their existing Ansible data. This helps provide personalized content recommendations that are more accurate and a better fit for your business.  

Model Customization is done using **Prompt Tuning:** Empowers organizations to tune its domain-specific LLM with their own Ansible data  

- **_Model customization empowers organizations to tune its domain-specific LLM with their own Ansible data_**
- **_Customization is beneficial for Ansible because of the many modules that might exist within an Ansible Playbook_**
- **_Discovery of unique modules increases quality code recommendations based on organization’s preferences_**

<img src="https://github.com/user-attachments/assets/c5d497ac-425b-4494-9a83-9e981285eb6a" alt="model-customization-example-png">

Don't miss out! Discover more information by clicking [**here**](https://cloud.ibm.com/docs/watsonx-code-assistant?topic=watsonx-code-assistant-tutorial-tune-ansible#tune-ansible-prereqs).

❗ **NOTE:** ❗
- _We recommend providing a data set with at least "1,000 samples = 1000 Ansible tasks" to generate better content recommendations._ 
- _If the data set includes more than one module, it is recommended to provide at least 100 samples per module(Does it mean 100 example of same module usage)_
- _You don't need to be a data scientist to effectively use watsonx Code Assistant. The UI provides helpful contextual information and guidance along the way._

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
  <summary>Here are a few key examples for your reference to enhance your experience👇</summary>

  <details>
    <summary>1. The clearer your Ansible task description, the better the inline prompt suggestions.</summary>

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

  </details> <!-- End of nested collapsible section 1 -->

  <details>
    <summary>2. Provide as much detail as possible in the task description, especially when copying/moving source and destination locations.</summary>

    - name: Copy chroot_tasks.j2 to dest as chroot_tasks.sh on remote host(s)
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.template:
        src: chroot_tasks.j2
        dest: /tmp/chroot_tasks.sh
        mode: '0755'
        owner: root
        group: root

  </details> <!-- End of nested collapsible section 2 -->

  <details>
    <summary>3. If you require an item to be present at its destination, you essentially need to command its placement there.</summary>

    - name: Ensure /var/tmp/ansible is in place
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.file:
        path: /var/tmp/ansible
        state: directory
        mode: '0755'

  </details> <!-- End of nested collapsible section 3 -->

  <details>
    <summary>4. If the suggestions or prompts don't return with the desired variable name, you can accept the suggestions and subsequently modify the variable name as usual.</summary>

    - name: Copy httpd.conf.j2 template to /etc/httpd/conf/
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.template:
        src: httpd.conf.j2
        dest: /etc/httpd/conf/httpd.conf
        mode: '0644'
        owner: root
        group: root

  </details> <!-- End of nested collapsible section 4 -->

  <details>
    <summary>5. Take the opportunity to create tasks with register data that was generated in the previous task.</summary>

    - name: "Get subscription status - Check if the system is already registered"
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.command: subscription-manager status
      register: subscription_status
      changed_when: false
      failed_when: false

  </details> <!-- End of nested collapsible section 5 -->

  <details>
    <summary>6. Ensure that if you require variables to be populated with values from previously filled variables, you declare this in the vars file and specify it in the Task description field.</summary>

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

  </details> <!-- End of nested collapsible section 6 -->

  <details>
    <summary>7. To automatically fill a service or content with a value from a variable, specify this requirement clearly in the task description.</summary>

    vars:
        welcome_note: "Welcome to Demo Web Server"

    - name: Create new file /var/www/html/index.html with content of var welcome_note
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.copy:
        content: "{{ welcome_note }}"
        dest: /var/www/html/index.html

  </details> <!-- End of nested collapsible section 7 -->

  <details>
    <summary>8. Ensure that clear and objective specifications are provided, especially when certain conditions must be met for a task to be completed, as commonly utilized in the `when:` condition.</summary>

    - name: Inserts/replaces the openat rule in /etc/audit/audit.rules when on x86_64
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.lineinfile:
        path: /etc/audit/audit.rules
        regexp: '^.*openat.*'
        line: '-a always,exit -F arch=b64 -S openat'
        state: present
      when: ansible_architecture == "x86_64"

  </details> <!-- End of nested collapsible section 8 -->

  <details>
    <summary>9. If any inline suggestions don't come up with the variable name you want, instead of accepting it and then changing the name of that variable, you can try changing the task name, there are several synonyms or alternative phrases that you can use it.</summary>

    - name: Print on screen the upgrade_inhibited var
      ansible.builtin.debug:
        msg: "{{ upgrade_inhibited }}"

    - name: Debug the upgrade_inhibited var
      ansible.builtin.debug:
        msg: "{{ upgrade_inhibited }}"

    - name: Output upgrade_inhibited var
      ansible.builtin.debug:
        msg: "{{ upgrade_inhibited }}"

    - name: Present upgrade_inhibited var
      ansible.builtin.debug:
        msg: "{{ upgrade_inhibited }}"

    - name: Create /var/tmp/ansible directory if it does not exist
      ansible.builtin.file:
        path: /var/tmp/ansible
        state: directory
        mode: '0755'

    - name: Generate /var/tmp/ansible directory if it does not exist
      ansible.builtin.file:
        path: /var/tmp/ansible
        state: directory
        mode: '0755'

    - name: Produce /var/tmp/ansible directory if it does not exist
      ansible.builtin.file:
        path: /var/tmp/ansible
        state: directory
        mode: '0755'

    - name: Form /var/tmp/ansible directory if it does not exist
      ansible.builtin.file:
        path: /var/tmp/ansible
        state: directory
        mode: '0755'

    - name: Craft /var/tmp/ansible directory if it does not exist
      ansible.builtin.file:
        path: /var/tmp/ansible
        state: directory
        mode: '0755'

    - name: Build /var/tmp/ansible directory if it does not exist
      ansible.builtin.file:
        path: /var/tmp/ansible
        state: directory
        mode: '0755'

    - name: Ensure /var/tmp/ansible is in place
      ansible.builtin.file:
        path: /var/tmp/ansible
        state: directory
        mode: '0755'

    - name: Guarantee /var/tmp/ansible is in place
      ansible.builtin.file:
        path: /var/tmp/ansible
        state: directory
        mode: '0755'

    - name: Ensure NTP service is running on RedHat Server(s)
      ansible.builtin.service:
        name: ntpd
        state: started
        enabled: true
      when: ansible_os_family == "RedHat"

  </details> <!-- End of nested collapsible section 9 -->

  <details>
    <summary>10. If you want to use values in a variable, you can call it in a few ways calling `{{ <VARIABLE_NAME> }}`, `var`, `variable` and so on...</summary>

    - name: Start and enable {{ wordpress_app }} services
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.service:
        name: "{{ item }}"
        state: started
        enabled: true
      loop:
        - "{{ wordpress_app }}"

  </details> <!-- End of nested collapsible section 10 -->

  <details>
    <summary>11. Previously highlighted, generative AI demonstrates robust contextual understanding. Consequently, when addressing specific tasks or activities, the AI adeptly maintains and adheres to established contextual parameters.</summary>

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

  </details> <!-- End of nested collapsible section 11 -->

  <details>
    <summary>12. If you require the execution of any module or command by the Ansible Controller node, ensure a clear and explicit specification.</summary>

    - name: Send an e-mail with official module using the Ansible controller node without superuser
      # Content suggestion provided by Ansible Lightspeed
      delegate_to: localhost
      community.general.mail:
        host: localhost
        port: 25
        subject: Ansible mail
        to: root
        body: Ansible mail body

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

  </details> <!-- End of nested collapsible section 12 -->

  <details>
    <summary>13. if the prompting suggestions doesn't make sense the Regular expression to find, replace something you can teach the Watsonx Code Assistant to use your regular expression, into the requisite module requested.</summary>

    - name: Find /etc/audit/ file(s) matching ^audit(\.rules|d\.conf)$
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.find:
        paths: /etc/audit/
        patterns: audit(\.rules|d\.conf)$
      register: audit_files

    or

    - name: Replace in the /etc/fstab file that matches (.*)cifs(.*)
      # Content suggestion provided by Ansible Lightspeed
      ansible.builtin.replace:
        path: /etc/fstab
        regexp: ^(.*)cifs(.*)
        replace: '#\1cifs\2'


  </details> <!-- End of nested collapsible section 13 -->

</details> <!-- End of top-level collapsible section -->

---

<img src="https://github.com/user-attachments/assets/6ac1505e-ac0a-4cf8-bf8f-74cb78a4e9ca" width="290" align="right" alt="prompt-guide-10">

**_Final Tips for an Optimal Usability Experience_**

**1** - _Although generative AI can be incredibly useful, it can sometimes produce answers that aren't exactly what you're looking for, or it can give you suggestions that seem off track. If this happens, don't hesitate to rewrite or reformulate your request. Your opinion is fundamental in guiding the AI to provide more precise, meaningful and relevant answers._

**2** - _Do not hesitate to utilize extensive prompts; in certain scenarios, this approach can enhance the accuracy of prompt suggestions generated by the AI. In summary, a well-crafted prompt is crucial for optimal outcomes._

---

## **_Question❓, Bug(issue) 🐛 or New Features(Contribute)_** 🙋‍♂️

<!-- Questions can be useful but optional, this gives you a place to say, "This is how to contact this project maintainers or create PRs -->
If you have any questions, issues or feature requests you can create a new issue [**> Click Here <**](https://github.com/IBM/watsonx-code-assistant-for-ansible/issues/)

---

## 📝 **_License_** 📝

[Apache License 2.0](http://www.apache.org/licenses/)

---

## **_Copyright_**

©️ Copyright IBM Corporation 2024