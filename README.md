<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Active Directory Home Lab – IT Support Portfolio</title>
  <style>
    :root { color-scheme: light; }
    body {
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      line-height: 1.55;
      margin: 0;
      padding: 32px 18px;
      background: #f6f7f9;
      color: #1f2937;
    }
    main {
      max-width: 980px;
      margin: 0 auto;
      background: #fff;
      border: 1px solid #e5e7eb;
      border-radius: 14px;
      padding: 28px;
      box-shadow: 0 6px 22px rgba(0,0,0,.06);
    }
    h1 { font-size: 1.9rem; margin: 0 0 10px; }
    h2 { font-size: 1.35rem; margin-top: 26px; }
    h3 { font-size: 1.1rem; margin-top: 18px; }
    p { margin: 10px 0; }
    .meta {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin: 14px 0 18px;
      padding: 14px;
      border-radius: 12px;
      background: #f9fafb;
      border: 1px solid #e5e7eb;
    }
    .pill {
      font-size: .9rem;
      padding: 6px 10px;
      border-radius: 999px;
      background: #eef2ff;
      border: 1px solid #e0e7ff;
    }
    ul { margin: 8px 0 8px 20px; }
    code, pre {
      font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, "Liberation Mono", monospace;
    }
    pre {
      background: #0b1020;
      color: #e5e7eb;
      padding: 14px;
      border-radius: 12px;
      overflow-x: auto;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin: 12px 0 6px;
      overflow: hidden;
      border-radius: 12px;
      border: 1px solid #e5e7eb;
    }
    th, td {
      padding: 10px 12px;
      border-bottom: 1px solid #e5e7eb;
      text-align: left;
      vertical-align: top;
      font-size: .95rem;
    }
    th {
      background: #f9fafb;
      font-weight: 650;
    }
    tr:last-child td { border-bottom: 0; }
    .note {
      background: #ecfeff;
      border: 1px solid #cffafe;
      padding: 12px 14px;
      border-radius: 12px;
      margin-top: 10px;
    }
    footer {
      margin-top: 26px;
      padding-top: 16px;
      border-top: 1px solid #e5e7eb;
      color: #6b7280;
      font-size: .95rem;
    }
  </style>
</head>

<body>
  <main>
    <header>
      <h1>🖥 Active Directory Home Lab – IT Support Portfolio</h1>
      <p>
        This page documents my hands-on Active Directory home lab built to simulate a real-world enterprise IT environment.
        The lab focuses on Level 1 / Level 2 support workflows, identity administration, and troubleshooting in a Windows domain.
      </p>

      <div class="meta" role="list" aria-label="Lab quick facts">
        <span class="pill" role="listitem"><strong>Domain:</strong> lab.local</span>
        <span class="pill" role="listitem"><strong>Domain Controller:</strong> DC01</span>
        <span class="pill" role="listitem"><strong>Client:</strong> CLIENT01</span>
        <span class="pill" role="listitem"><strong>Platform:</strong> VirtualBox</span>
        <span class="pill" role="listitem"><strong>Network:</strong> Internal Network</span>
      </div>
    </header>

    <section>
      <h2>📌 Overview</h2>
      <p>This lab demonstrates core IT Support competencies, including:</p>
      <ul>
        <li>User provisioning and lifecycle management</li>
        <li>Security group design using the AGDLP model</li>
        <li>Password resets, account unlocks, and access changes</li>
        <li>Domain join and domain login validation</li>
        <li>DNS checks and troubleshooting</li>
        <li>Group Policy practice (GPO scope, enforcement, and testing)</li>
        <li>Basic PowerShell administration</li>
      </ul>
    </section>

    <section>
      <h2>🏗 Lab Environment Architecture</h2>

      <h3>Domain Information</h3>
      <ul>
        <li><strong>Domain Name:</strong> <code>lab.local</code></li>
        <li><strong>Domain Controller:</strong> <code>DC01</code></li>
        <li><strong>Client Machine:</strong> <code>CLIENT01</code></li>
        <li><strong>Server OS:</strong> Windows Server 2022 (Evaluation)</li>
        <li><strong>Client OS:</strong> Windows 10/11</li>
        <li><strong>Virtualization Platform:</strong> VirtualBox</li>
        <li><strong>Network Type:</strong> Internal Network</li>
      </ul>

      <h3>IP Configuration (Static DC Setup)</h3>
      <table aria-label="IP configuration table">
        <thead>
          <tr>
            <th>Machine</th>
            <th>Role</th>
            <th>IP Address</th>
            <th>DNS</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>DC01</td>
            <td>Domain Controller</td>
            <td>192.168.10.10</td>
            <td>192.168.10.10</td>
          </tr>
          <tr>
            <td>CLIENT01</td>
            <td>Domain Client</td>
            <td>192.168.10.x</td>
            <td>192.168.10.10</td>
          </tr>
        </tbody>
      </table>

      <div class="note">
        <strong>Note:</strong> The Domain Controller uses a static IP and is configured as the DNS server for the domain.
        This mirrors common enterprise practice and prevents authentication issues caused by DNS mismatches.
      </div>
    </section>

    <section>
      <h2>🔧 Core Skills Demonstrated</h2>

      <h3>1️⃣ Active Directory Administration</h3>
      <ul>
        <li>Created Organizational Units (OUs)</li>
        <li>Created and managed users</li>
        <li>Disabled / re-enabled accounts</li>
        <li>Forced password change at next logon</li>
        <li>Reset passwords</li>
        <li>Unlocked locked accounts</li>
        <li>Moved users between OUs</li>
      </ul>

      <h3>2️⃣ Security Group Strategy (AGDLP Model)</h3>
      <p>Implemented structured access control:</p>
      <pre><code>User → Global Group → Domain Local Group → NTFS Permissions</code></pre>

      <p>Example mapping:</p>
      <pre><code>JDavis
   ↓
GG_DevTeam_Users
   ↓
DL_DevShare_RW
   ↓
\\FileServer\Dev (Modify)</code></pre>

      <p>
        This approach reduces ACL sprawl and mirrors enterprise best practices by keeping permissions assigned to groups,
        not individual users.
      </p>

      <h3>3️⃣ Client Domain Integration</h3>
      <ul>
        <li>Joined <code>CLIENT01</code> to <code>lab.local</code></li>
        <li>Logged in with domain user credentials</li>
        <li>Verified DNS resolution and authentication</li>
        <li>Confirmed domain trust relationship</li>
      </ul>

      <h3>4️⃣ DNS Validation &amp; Troubleshooting</h3>
      <p>Performed checks using:</p>
      <ul>
        <li><code>ipconfig /all</code></li>
        <li><code>nslookup</code></li>
        <li><code>ping DC01</code></li>
        <li>Verified the client DNS server points to the Domain Controller</li>
      </ul>

      <p>Troubleshooting scenarios included:</p>
      <ul>
        <li>Destination host unreachable</li>
        <li>Incorrect DNS configuration</li>
        <li>Incorrect subnet configuration</li>
      </ul>

      <h3>5️⃣ Group Policy Practice</h3>
      <ul>
        <li>Password policy enforcement</li>
        <li>Account lockout policy</li>
        <li>OU-based policy application</li>
        <li>Policy refresh testing using <code>gpupdate /force</code></li>
      </ul>

      <h3>6️⃣ PowerShell Administration</h3>
      <ul>
        <li>Creating users via PowerShell</li>
        <li>Bulk account creation</li>
        <li>Adding users to security groups</li>
        <li>Querying AD objects</li>
      </ul>

      <p>Example command:</p>
      <pre><code>New-ADUser -Name "John Davis" -SamAccountName JDavis -AccountPassword (ConvertTo-SecureString "N0rthbridge!2026" -AsPlainText -Force) -Enabled $true</code></pre>
    </section>

    <section>
      <h2>🧠 Real-World IT Scenarios Simulated</h2>
      <ul>
        <li>Employee onboarding</li>
        <li>Employee termination (account disable)</li>
        <li>Password expiration enforcement</li>
        <li>Access modification</li>
        <li>Domain login failures</li>
        <li>Network misconfiguration</li>
        <li>DNS resolution issues</li>
      </ul>
    </section>

    <section>
      <h2>🎯 What This Lab Proves</h2>
      <p>This lab demonstrates practical ability to:</p>
      <ul>
        <li>Support Windows domain environments</li>
        <li>Manage Active Directory objects safely and consistently</li>
        <li>Follow enterprise group permission models (AGDLP)</li>
        <li>Troubleshoot authentication and networking issues</li>
        <li>Document and execute structured IT workflows</li>
      </ul>

      <p>These are core skills required in:</p>
      <ul>
        <li>Help Desk (Level 1)</li>
        <li>Desktop Support (Level 2)</li>
        <li>Junior Systems Administrator roles</li>
      </ul>
    </section>

    <section>
      <h2>📈 Next Steps / Planned Enhancements</h2>
      <ul>
        <li>File server role implementation</li>
        <li>Shared folder permission audits</li>
        <li>WSUS configuration</li>
        <li>Ticketing system integration (Jira Service Management lab)</li>
        <li>Advanced PowerShell automation</li>
      </ul>
    </section>

    <footer>
      <h2>👤 Author</h2>
      <p>
        <strong>Paul Stewart</strong><br />
        IT Support Professional<br />
        Toronto, ON
      </p>
    </footer>
  </main>
</body>
</html>
