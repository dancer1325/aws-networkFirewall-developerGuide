* AWS Network Firewall
  * := network firewall + intrusion detection & prevention service | your VPC
    * firewall is
      * stateful
        * -- via -- [Suricata](https://suricata.io/)
          * := open source intrusion prevention system (IPS)
          * see [stateful-rule-groups-ips](stateful-rule-groups-ips.md)
      * managed
  * allows
    * filtering traffic (incoming & outgoing) | VPC level
      * VPC level -- includes -- 
        * internet gateway,
        * NAT gateway,
        * over
          * VPN or
          * AWS Direct Connect
    * monitoring & protecting -- your -- Amazon VPC traffic / allowed ways
      * pass traffic -- through ONLY from -- known
        * AWS service domains or
        * IP address endpoints
      * use
        * custom lists of known bad domains -- to limit the -- types of domain names / your applications can access
        * stateful protocol detection -- to filter -- protocols (_Example:_ HTTPS) 
      * perform deep packet inspection -- about -- traffic /
        * entering your VPC or
        * leaving your VPC
  * how to enable it?
    * perform steps |
      * Amazon VPC
      * Network Firewall
        * see [how-it-works](how-it-works.md)
  * used by
    * AWS Firewall Manager
      * allows
        * centrally configure & manage your firewalls -- ACROSS your -- accounts & applications | AWS Organizations
          * 👀== manage multiple accounts' firewalls -- via -- 1! account | Firewall Manager 👀 
      * see [AWS Firewall Manager](https://docs.aws.amazon.com/waf/latest/developerguide/fms-chapter.html) 
  * resources / -- managed by -- Network Firewall
    * Firewall
      * provides
        * traffic filtering logic -- for the -- VPC's subnets
    * FirewallPolicy
      * == rules + other settings -- for a -- firewall
    * RuleGroup
      * == set of rules + actions to take  
        * rules / match -- against -- VPC traffic
      * has its own ARN
      * types
        * stateless
          * == inspect a network traffic packet / WITHOUT taking in account the
            * context of the other packets | traffic flow,
            * direction of flow,
            * ANY other information / -- NOT provided by the -- packet itself
        * stateful
          * == inspect a network traffic packet | context of their traffic flow
  * concepts
    * Firewall subnet
      * := subnet / -- designated for exclusive use by -- Network Firewall's firewall endpoint
        * firewall endpoint
          * 👀can NOT filter traffic coming into OR going out of the subnet 👀 
      * uses
        * ONLY for Network Firewall
    * Route table
      * == set of rules
      * uses
        * determine where network traffic -- is -- directed
      * configure it | VPC

* ways to create, access, and manage your Network Firewall resources (firewall, firewall policy, and rule group)
  * AWS Management Console
    * TODO:– Provides a web interface for managing the service. The procedures throughout this guide explain how to use the AWS Management Console to perform tasks for Network Firewall. You can access the AWS Management Console at https://aws.amazon.com/console. To access Network Firewall using the console:
  
    ```
    https://<region>.console.aws.amazon.com/network-firewall/home
    ```
  * AWS CLI
    * – Provides commands for a broad set of AWS services, including Network Firewall. The CLI is supported on Windows, macOS, and Linux. For more information, see the AWS Command Line Interface User Guide. To access Network Firewall using the CLI endpoint:
  
    ```
    aws network-firewall
    ```
  * AWS Network Firewall API
    * – Provides a RESTful API. The REST API requires you to handle connection details, such as calculating signatures, handling request retries, and handling errors. For more information, see AWS APIs and the AWS Network Firewall API Reference. To access Network Firewall, use the following REST API endpoint:
  
    ```
    https://network-firewall.<region>.amazonaws.com
    ```
  * AWS SDKs
    * – Provide language-specific APIs. If you're using a programming language that AWS provides an SDK for, you can use the SDK to access AWS Network Firewall. The SDKs handle many of the connection details, such as calculating signatures, handling request retries, and handling errors. They integrate easily with your development environment, and provide easy access to Network Firewall commands. For more information, see Tools for Amazon Web Services.
  
  * AWS CloudFormation
    * – Helps you model and set up your Amazon Web Services resources so that you can spend less time managing those resources and more time focusing on your applications that run in AWS. You create a template that describes all the AWS resources that you want and AWS CloudFormation takes care of provisioning and configuring those resources for you. For more information, see Network Firewall resource type reference in the AWS CloudFormation User Guide.
  
  * AWS Tools for Windows PowerShell
    * – Let developers and administrators manage their AWS services and resources in the PowerShell scripting environment. For more information, see the AWS Tools for Windows PowerShell User Guide.

* TODO: