<h1 class="code-line" data-line-start=0 data-line-end=1 ><a id="Runbook_for_Initial_Cluster_Configuration_on_Cloud_oneFS_0"></a>Runbook for Initial Cluster Configuration on Cloud oneFS</h1>
<p class="has-line-data" data-line-start="2" data-line-end="3">Below are the steps that need to be performed manually in order to provide the minimal configuration needed to access the cluster and proceed. These steps can be followed exclusively on the console.</p>
<p class="has-line-data" data-line-start="4" data-line-end="5">Upon successful installation of Isilon OneFS, the user will receive a sequence of prompts as shown below:</p>
<pre><code class="has-line-data" data-line-start="6" data-line-end="23" class="language-sh">Welcome to the Isilon IQ configuration wizard.
Copyright (c) <span class="hljs-number">2001</span>-<span class="hljs-number">2020</span> Dell Inc. All Rights Reserved.
Enter <span class="hljs-string">'help'</span> at any prompt <span class="hljs-keyword">for</span> additional information on that step.
Enter <span class="hljs-string">'back'</span> at any prompt to <span class="hljs-built_in">return</span> to previous step.
Enter <span class="hljs-string">'quit'</span> at any prompt to discard all changes.
Enter <span class="hljs-string">'manual'</span> at any prompt to switch to manual mode (console).

    Node build: Isilon OneFS 9.1.0.14 B_9_1_0_003(RELEASE) 
	Node serial number: SV200-153267-4182

Select an option:
    [ <span class="hljs-number">1</span>] Create a new cluster
    [ <span class="hljs-number">2</span>] Join an existing cluster
    [ <span class="hljs-number">3</span>] Exit wizard and configure manually
    [ <span class="hljs-number">4</span>] Reboot into SmartLock Compliance mode
Wizard &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="23" data-line-end="24">Type in <code>1</code>, and press <code>enter</code> to continue creating a new cluster. Next,</p>
<pre><code class="has-line-data" data-line-start="26" data-line-end="46" class="language-sh">*** IMPORTANT INFORMATION - PLEASE READ CAREFULLY ***

Congratulations on your new Dell EMC purchase!

Your purchase and use of this Dell EMC product is subject to and governed
by the Dell EMC Commercial Terms of Sale, unless you have a separate written
agreement with Dell EMC that specifically applies to your order, and the End
User License Agreement (E-EULA), which are each presented below in the
following order:

*       Commercial Terms of Sale
*       End User License Agreement (E-EULA)

The Commercial Terms of Sale for the United States are presented below and
are also available online at the website below that corresponds to the country
in which this product was purchased.

By the act of clicking "I accept," you agree (or re-affirm your agreement to)
the foregoing terms and conditions.  To the extent that Dell Inc. or any Dell
Inc.'s direct or indirect subsidiary ("Dell") is deemed under applicable law
to have accepted an offer by you: (a) Dell hereby objects to and rejects all
additional or inconsistent terms that may be contained in any purchase order
or other documentation submitted by you in connection with your order; and (b)
--More--(2%)





Do you accept the EULA? [no]
</code></pre>
<p class="has-line-data" data-line-start="47" data-line-end="48">Type in <code>yes</code> and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="50" data-line-end="53" class="language-sh">Please change the root password from the default.
Please enter new password <span class="hljs-keyword">for</span> root:
</code></pre>
<p class="has-line-data" data-line-start="54" data-line-end="55">Type in appropriate new password, and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="57" data-line-end="59" class="language-sh">Please re-enter password <span class="hljs-keyword">for</span> root: 
</code></pre>
<p class="has-line-data" data-line-start="60" data-line-end="61">Re-type the password, and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="63" data-line-end="68" class="language-sh">Password changed.

Please change the UI admin password from the default.
Please enter new password <span class="hljs-keyword">for</span> admin:
</code></pre>
<p class="has-line-data" data-line-start="69" data-line-end="70">Type in appropriate new password for UI admin, and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="72" data-line-end="74" class="language-sh">Please re-enter password <span class="hljs-keyword">for</span> admin:
</code></pre>
<p class="has-line-data" data-line-start="75" data-line-end="76">Re-type the password, and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="78" data-line-end="84" class="language-sh">Password changed.


Enter a new name <span class="hljs-keyword">for</span> the cluster:
Configure name &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="85" data-line-end="86">Type in the appropriate cluster name, (note: in this example runbook we are using cluster name as <code>vonefs-black-canary</code>). Press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="88" data-line-end="94" class="language-sh">!! WARNING: Limit cluster name to <span class="hljs-number">11</span> characters or less when the
!! NetBIOS Name Service is enabled to avoid name truncation. Isilon
!! uses up to <span class="hljs-number">4</span> characters <span class="hljs-keyword">for</span> individual node names.

Proceed with cluster name vonefs-black-canary? [yes]
</code></pre>
<p class="has-line-data" data-line-start="95" data-line-end="96">Type in <code>yes</code> and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="98" data-line-end="126" class="language-sh">Cluster name <span class="hljs-built_in">set</span> to vonefs-black-canary

Cluster encoding:
    [ <span class="hljs-number">1</span>] Windows-SJIS
    [ <span class="hljs-number">2</span>] Windows-<span class="hljs-number">949</span>
    [ <span class="hljs-number">3</span>] Windows-<span class="hljs-number">1252</span>
    [ <span class="hljs-number">4</span>] EUC-KR
    [ <span class="hljs-number">5</span>] EUC-JP
    [ <span class="hljs-number">6</span>] EUC-JP-MS
    [ <span class="hljs-number">7</span>] UTF-<span class="hljs-number">8</span>-MAC
    [ <span class="hljs-number">8</span>] UTF-<span class="hljs-number">8</span>
    [ <span class="hljs-number">9</span>] ISO-<span class="hljs-number">8859</span>-<span class="hljs-number">1</span> (Latin-<span class="hljs-number">1</span>)
    [<span class="hljs-number">10</span>] ISO-<span class="hljs-number">8859</span>-<span class="hljs-number">2</span> (Latin-<span class="hljs-number">2</span>)
    [<span class="hljs-number">11</span>] ISO-<span class="hljs-number">8859</span>-<span class="hljs-number">3</span> (Latin-<span class="hljs-number">3</span>)
    [<span class="hljs-number">12</span>] ISO-<span class="hljs-number">8859</span>-<span class="hljs-number">4</span> (Latin-<span class="hljs-number">4</span>)
    [<span class="hljs-number">13</span>] ISO-<span class="hljs-number">8859</span>-<span class="hljs-number">5</span> (Cyrillic)
    [<span class="hljs-number">14</span>] ISO-<span class="hljs-number">8859</span>-<span class="hljs-number">6</span> (Arabic)
    [<span class="hljs-number">15</span>] ISO-<span class="hljs-number">8859</span>-<span class="hljs-number">7</span> (Greek)
    [<span class="hljs-number">16</span>] ISO-<span class="hljs-number">8859</span>-<span class="hljs-number">8</span> (Hebrew)
    [<span class="hljs-number">17</span>] ISO-<span class="hljs-number">8859</span>-<span class="hljs-number">9</span> (Latin-<span class="hljs-number">5</span>)
    [<span class="hljs-number">18</span>] ISO-<span class="hljs-number">8859</span>-<span class="hljs-number">10</span> (Latin-<span class="hljs-number">6</span>)
    [<span class="hljs-number">19</span>] ISO-<span class="hljs-number">8859</span>-<span class="hljs-number">13</span> (Latin-<span class="hljs-number">7</span>)
    [<span class="hljs-number">20</span>] ISO-<span class="hljs-number">8859</span>-<span class="hljs-number">14</span> (Latin-<span class="hljs-number">8</span>)
    [<span class="hljs-number">21</span>] ISO-<span class="hljs-number">8859</span>-<span class="hljs-number">15</span> (Latin-<span class="hljs-number">9</span>)
    [<span class="hljs-number">22</span>] ISO-<span class="hljs-number">8859</span>-<span class="hljs-number">16</span> (Latin-<span class="hljs-number">10</span>)
    [Enter] Use current encoding: utf-<span class="hljs-number">8</span>
Configure encoding &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="127" data-line-end="128">Type in <code>8</code> and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="130" data-line-end="142" class="language-sh">Encoding <span class="hljs-built_in">set</span> to utf-<span class="hljs-number">8</span>

Configure interface int<span class="hljs-operator">-a</span>:
    [ <span class="hljs-number">1</span>] Configure netmask
    [ <span class="hljs-number">2</span>] Configure MTU
    [ <span class="hljs-number">3</span>] Configure int<span class="hljs-operator">-a</span> IP ranges
    [Enter] Keep the current configuration:
               Netmask: (not <span class="hljs-built_in">set</span>)
                   MTU: <span class="hljs-number">1460</span> (shared)
             IP ranges: (not <span class="hljs-built_in">set</span>)
Configure interface int<span class="hljs-operator">-a</span> &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="143" data-line-end="144">Type in <code>1</code>, and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="146" data-line-end="149" class="language-sh">Enter a new netmask
Configure int<span class="hljs-operator">-a</span> netmask &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="150" data-line-end="151">Type in the appropriate netmask, (note: in this example runbook we are using netmask as <code>255.255.248.0</code>), and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="153" data-line-end="163" class="language-sh">Configure interface int<span class="hljs-operator">-a</span>:
    [ <span class="hljs-number">1</span>] Configure netmask
    [ <span class="hljs-number">2</span>] Configure MTU
    [ <span class="hljs-number">3</span>] Configure int<span class="hljs-operator">-a</span> IP ranges
    [Enter] Keep the current configuration:
               Netmask: <span class="hljs-number">255.255</span>.<span class="hljs-number">248.0</span>
                   MTU: <span class="hljs-number">1460</span> (shared)
             IP ranges: (not <span class="hljs-built_in">set</span>)
Configure interface int<span class="hljs-operator">-a</span> &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="164" data-line-end="165">Type in <code>3</code>, and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="167" data-line-end="174" class="language-sh">Configure int<span class="hljs-operator">-a</span> IP ranges
    [ <span class="hljs-number">1</span>] Add an IP range
    [ <span class="hljs-number">2</span>] Delete an IP range
    [Enter] Keep the current IP ranges:
             IP ranges: (not <span class="hljs-built_in">set</span>)
Configure int<span class="hljs-operator">-a</span> IP ranges &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="175" data-line-end="176">Type in <code>1</code>, and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="178" data-line-end="181" class="language-sh">Enter the low IP address of the range to add:
Low IP address (add) &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="182" data-line-end="183">Type in appropriate low IP address, (note: in this example runbook we are using low IP address as: <code>10.3.104.2</code>), and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="185" data-line-end="188" class="language-sh">Enter the high IP address of the range:
High IP address (add) &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="189" data-line-end="190">Press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="192" data-line-end="199" class="language-sh">Configure int<span class="hljs-operator">-a</span> IP ranges
    [ <span class="hljs-number">1</span>] Add an IP range
    [ <span class="hljs-number">2</span>] Delete an IP range
    [Enter] Keep the current IP ranges:
             IP ranges: <span class="hljs-number">10.3</span>.<span class="hljs-number">104.2</span>-<span class="hljs-number">10.3</span>.<span class="hljs-number">104.2</span>
Configure int<span class="hljs-operator">-a</span> IP ranges &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="200" data-line-end="201">Press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="203" data-line-end="213" class="language-sh">Configure interface int<span class="hljs-operator">-a</span>:
    [ <span class="hljs-number">1</span>] Configure netmask
    [ <span class="hljs-number">2</span>] Configure MTU
    [ <span class="hljs-number">3</span>] Configure int<span class="hljs-operator">-a</span> IP ranges
    [Enter] Keep the current configuration:
               Netmask: <span class="hljs-number">255.255</span>.<span class="hljs-number">248.0</span>
                   MTU: <span class="hljs-number">1460</span> (shared)
             IP ranges: <span class="hljs-number">10.3</span>.<span class="hljs-number">104.2</span>-<span class="hljs-number">10.3</span>.<span class="hljs-number">104.2</span>
Configure interface int<span class="hljs-operator">-a</span> &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="214" data-line-end="215">Press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="217" data-line-end="223" class="language-sh">Configure external subnet
    [ <span class="hljs-number">1</span>] ext-<span class="hljs-number">1</span> - External interface
    [ <span class="hljs-number">2</span>] Use internal interface <span class="hljs-keyword">for</span> external subnet
    [Enter] Exit configuring external network.
Configure external subnet &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="224" data-line-end="225">Type in <code>1</code>, and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="227" data-line-end="237" class="language-sh">Configure interface ext-<span class="hljs-number">1</span>:
    [ <span class="hljs-number">1</span>] Configure netmask
    [ <span class="hljs-number">2</span>] Configure MTU
    [ <span class="hljs-number">3</span>] Configure ext-<span class="hljs-number">1</span> IP ranges
    [Enter] Keep the current configuration:
               Netmask: (not <span class="hljs-built_in">set</span>)
                   MTU: <span class="hljs-number">1500</span>
             IP ranges: (not <span class="hljs-built_in">set</span>)
Configure interface ext-<span class="hljs-number">1</span> &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="237" data-line-end="238">Type in <code>1</code>, and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="240" data-line-end="243" class="language-sh">Enter a new netmask
Configure ext-<span class="hljs-number">1</span> netmask &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="244" data-line-end="245">Type in appropriate netmask, (note: in this example runbook we are using netmask as: <code>255.255.248.0</code>), and press enter to continue.</p>
<pre><code class="has-line-data" data-line-start="247" data-line-end="257" class="language-sh">Configure interface ext-<span class="hljs-number">1</span>:
    [ <span class="hljs-number">1</span>] Configure netmask
    [ <span class="hljs-number">2</span>] Configure MTU
    [ <span class="hljs-number">3</span>] Configure ext-<span class="hljs-number">1</span> IP ranges
    [Enter] Keep the current configuration:
               Netmask: <span class="hljs-number">255.255</span>.<span class="hljs-number">248.0</span>
                   MTU: <span class="hljs-number">1500</span>
             IP ranges: (not <span class="hljs-built_in">set</span>)
Configure interface ext-<span class="hljs-number">1</span> &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="258" data-line-end="259">Type in <code>3</code>, and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="261" data-line-end="268" class="language-sh">Configure external IP ranges
    [ <span class="hljs-number">1</span>] Add an IP range
    [ <span class="hljs-number">2</span>] Delete an IP range
    [Enter] Keep the current IP ranges:
             IP ranges: (not <span class="hljs-built_in">set</span>)
Configure ext-<span class="hljs-number">1</span> IP ranges &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="269" data-line-end="270">Type in <code>1</code>, and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="272" data-line-end="275" class="language-sh">Enter the low IP address of the range to add:
Low IP address (add) &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="276" data-line-end="277">Type in appropriate low IP address, (note: in this example runbook we are using low IP address as: <code>10.3.96.2</code>), and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="279" data-line-end="282" class="language-sh">Enter the high IP address of the range:
High IP address (add) &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="283" data-line-end="284">Press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="286" data-line-end="293" class="language-sh">Configure external IP ranges
    [ <span class="hljs-number">1</span>] Add an IP range
    [ <span class="hljs-number">2</span>] Delete an IP range
    [Enter] Keep the current IP ranges:
             IP ranges: <span class="hljs-number">10.3</span>.<span class="hljs-number">96.2</span>-<span class="hljs-number">10.3</span>.<span class="hljs-number">96.2</span>
Configure ext-<span class="hljs-number">1</span> IP ranges &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="294" data-line-end="295">Press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="297" data-line-end="307" class="language-sh">Configure interface ext-<span class="hljs-number">1</span>:
    [ <span class="hljs-number">1</span>] Configure netmask
    [ <span class="hljs-number">2</span>] Configure MTU
    [ <span class="hljs-number">3</span>] Configure ext-<span class="hljs-number">1</span> IP ranges
    [Enter] Keep the current configuration:
               Netmask: <span class="hljs-number">255.255</span>.<span class="hljs-number">248.0</span>
                   MTU: <span class="hljs-number">1500</span>
             IP ranges: <span class="hljs-number">10.3</span>.<span class="hljs-number">96.2</span>-<span class="hljs-number">10.3</span>.<span class="hljs-number">96.2</span>
Configure interface ext-<span class="hljs-number">1</span> &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="308" data-line-end="309">Press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="311" data-line-end="314" class="language-sh">Enter default gateway:
Configure default gateway &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="315" data-line-end="316">Type in appropriate default gateway, (note: in this example runbook we are using gateway as <code>10.3.96.1</code>), and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="318" data-line-end="326" class="language-sh">Configure SmartConnect settings
    [ <span class="hljs-number">1</span>] SmartConnect zone name
    [ <span class="hljs-number">2</span>] SmartConnect service IP
    [Enter] Keep the current SmartConnect settings:
    SmartConnect zone name: (not <span class="hljs-built_in">set</span>)
     SmartConnect service IP: (not <span class="hljs-built_in">set</span>)
Configure SmartConnect settings &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="327" data-line-end="328">Type in <code>1</code>, and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="330" data-line-end="333" class="language-sh">Enter SmartConnect zone name
SmartConnect zone name &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="334" data-line-end="335">Type in appropriate SmartConnect zone name, (note: in this example runbook we are using <code>black-canary.onefs</code>), and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="337" data-line-end="345" class="language-sh">Configure SmartConnect settings
    [ <span class="hljs-number">1</span>] SmartConnect zone name
    [ <span class="hljs-number">2</span>] SmartConnect service IP
    [Enter] Keep the current SmartConnect settings:
    SmartConnect zone name: black-canary.onefs
     SmartConnect service IP: (not <span class="hljs-built_in">set</span>)
Configure SmartConnect settings &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="345" data-line-end="346">Type in <code>2</code>, and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="348" data-line-end="351" class="language-sh">Enter SmartConnect service IP
SmartConnect service IP &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="352" data-line-end="353">Type in appropriate service IP, (note, in this example runbook we are using <code>10.3.96.3</code> as service IP), and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="355" data-line-end="363" class="language-sh">Configure SmartConnect settings
    [ <span class="hljs-number">1</span>] SmartConnect zone name
    [ <span class="hljs-number">2</span>] SmartConnect service IP
    [Enter] Keep the current SmartConnect settings:
    SmartConnect zone name: black-canary.onefs
     SmartConnect service IP: <span class="hljs-number">10.3</span>.<span class="hljs-number">96.3</span>
Configure SmartConnect settings &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="364" data-line-end="365">Press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="367" data-line-end="375" class="language-sh">Configure DNS settings
    [ <span class="hljs-number">1</span>] DNS servers
    [ <span class="hljs-number">2</span>] Search domains
    [Enter] Keep current DNS settings:
         DNS servers: (not <span class="hljs-built_in">set</span>)
      Search domains: (not <span class="hljs-built_in">set</span>)
Configure DNS settings &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="376" data-line-end="377">Press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="379" data-line-end="385" class="language-sh">Configure external subnet
    [ <span class="hljs-number">1</span>] ext-<span class="hljs-number">1</span> - External interface
    [ <span class="hljs-number">2</span>] Use internal interface <span class="hljs-keyword">for</span> external subnet
    [Enter] Exit configuring external network.
Configure external subnet &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="386" data-line-end="387">Press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="389" data-line-end="395" class="language-sh">Configure cluster date and time
    [ <span class="hljs-number">1</span>] Configure time zone
    [ <span class="hljs-number">2</span>] Configure day and time
    [Enter] Keep the current date and time: <span class="hljs-number">2023</span>/<span class="hljs-number">03</span>/<span class="hljs-number">15</span> <span class="hljs-number">10</span>:<span class="hljs-number">04</span>:<span class="hljs-number">32</span> GMT.
Configure date &gt;&gt;&gt; 
</code></pre>
<p class="has-line-data" data-line-start="396" data-line-end="397">Press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="399" data-line-end="405" class="language-sh">Configure cluster join mode
    [ <span class="hljs-number">1</span>] Manual
    [ <span class="hljs-number">2</span>] Secure
    [Enter] Keep the current join mode: Manual
Configure join mode &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="406" data-line-end="407">Type in <code>1</code>, and press <code>enter</code> to continue.</p>
<pre><code class="has-line-data" data-line-start="409" data-line-end="425" class="language-sh">Join mode <span class="hljs-built_in">set</span> to Manual.
You have made the following configuration changes:

Cluster name           : (not <span class="hljs-built_in">set</span>) -&gt; vonefs-black-canary
Encoding               : (not <span class="hljs-built_in">set</span>) -&gt; utf-<span class="hljs-number">8</span>
int<span class="hljs-operator">-a</span> netmask          : (not <span class="hljs-built_in">set</span>) -&gt; <span class="hljs-number">255.255</span>.<span class="hljs-number">248.0</span>
int<span class="hljs-operator">-a</span> IP ranges        : (not <span class="hljs-built_in">set</span>) -&gt; { <span class="hljs-number">10.3</span>.<span class="hljs-number">104.2</span>-<span class="hljs-number">10.3</span>.<span class="hljs-number">104.2</span> }
ext-<span class="hljs-number">1</span> netmask          : (not <span class="hljs-built_in">set</span>) -&gt; <span class="hljs-number">255.255</span>.<span class="hljs-number">248.0</span>
ext-<span class="hljs-number">1</span> IP range         : (not <span class="hljs-built_in">set</span>) -&gt; { <span class="hljs-number">10.3</span>.<span class="hljs-number">96.2</span>-<span class="hljs-number">10.3</span>.<span class="hljs-number">96.2</span> }
ext-<span class="hljs-number">1</span> gateway          : (not <span class="hljs-built_in">set</span>) -&gt; <span class="hljs-number">10.3</span>.<span class="hljs-number">96.1</span>
SmartConnect zone name : (not <span class="hljs-built_in">set</span>) -&gt; black-canary.onefs
SmartConnect service IP: (not <span class="hljs-built_in">set</span>) -&gt; <span class="hljs-number">10.3</span>.<span class="hljs-number">96.3</span>

Do you wish to commit these changes? [yes]
Commit changes? &gt;&gt;&gt;
</code></pre>
<p class="has-line-data" data-line-start="426" data-line-end="427">Type in <code>yes</code>, and press <code>enter</code> to finish the initial setup wizard.</p>
