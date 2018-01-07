IAM
==

- What kinds of security credentials can IAM users have?

  IAM users can have any combination of credentials that AWS supports, such as an AWS access key, X.509 certificate, SSH key, password for web app logins, or an MFA device


- Users are global entities, like an AWS account is today.

  Permissions can restrict a users access to a certain region

- What kind of key rotation is supported for IAM users?

  User access keys and X.509 certificates can be rotated just as they are for an AWS account's root access identifiers. You can manage and rotate programmatically a user's access keys and X.509 certificates via the IAM APIs, AWS CLI, or IAM console.

- Where can I use my SSH keys?

  Currently, IAM users can use their SSH keys only with AWS CodeCommit to access their repositories.

- Which character sets can I use for IAM user names?
  You can only use ASCII characters for IAM entities.

- Can I set usage quotas on IAM users?

  No. All limits are on the AWS account as a whole.

Roles
--

- What is an IAM role?

  An IAM role is an IAM entity that defines a set of permissions for making AWS service requests. IAM roles are not associated with a specific user or group. Instead, trusted entities assume roles, such as IAM users, applications, or AWS services such as EC2.

- How do I assume an IAM role?

  You assume an IAM role by calling the AWS Security Token Service (STS) AssumeRole APIs (in other words, AssumeRole, AssumeRoleWithWebIdentity, and AssumeRoleWithSAML)

- How many policies can I attach to an IAM role?

  For inline policies: You can add as many inline policies as you want to a user, role, or group, but the total aggregate policy size (the sum size of all inline policies) per entity cannot exceed the following limits:

      User policy size cannot exceed 2,048 characters.
      Role policy size cannot exceed 10,240 characters.
      Group policy size cannot exceed 5,120 characters.

  For managed policies: You can add up to 10 managed policies to a user, role, or group. The size of each managed policy cannot exceed 6,144 characters

- How many IAM roles can I create?

  You are limited to 1,000 IAM roles under your AWS account (Can be increased upon request)

- Can I associate more than one IAM role with an EC2 instance?

  No. You can only associate one IAM role with an EC2 instance at this time.

Policies
--

- IAM JSON Policy Evaluation Logic

  When a request is made, the AWS service decides whether a given request should be allowed or denied. The evaluation logic follows these rules:

  - By default, all requests are denied. (In general, requests made using the account credentials for resources in the account are always allowed.)

  - An explicit allow overrides this default.

  - An explicit deny overrides any allows.

  The distinction between a request being denied by default and an explicit deny in a policy is important. By default, a request is denied, but this can be overridden by an allow. In contrast, if a policy explicitly denies a request, that deny can't be overridden.

Sign In
--

- What is an AWS account alias?

  The account alias is a name you define to make it more convenient to identify your account. You can create an alias using the IAM APIs, AWS Command Line Tools, or the IAM console. You can have one alias per AWS account.

- Which AWS sites can IAM users access?

  IAM users can sign in to the following AWS sites:

      AWS Management Console
      AWS Forums
      AWS Support Center
      AWS Marketplace

- Can users SSH to EC2 instances using their AWS user name and password?

    No. User security credentials created with IAM are not supported for direct authentication to customer EC2 instances. Managing EC2 SSH credentials is the customer’s responsibility within the EC2 console.

Temporary credentials
--

- What are temporary security credentials?

  Temporary security credentials consist of the AWS access key ID, secret access key, and security token. Temporary security credentials are valid for a specified duration and for a specific set of permissions. Temporary security credentials are sometimes simply referred to as tokens. Tokens can be requested for IAM users or for federated users you manage in your own corporate directory.

- How can I request temporary security credentials for federated users?

  You can call the GetFederationToken, AssumeRole, AssumeRoleWithSAML, or AssumeRoleWithWebIdentity STS APIs

- How can IAM users request temporary security credentials for their own use?

  IAM users can request temporary security credentials for their own use by calling the AWS STS GetSessionToken API. The default expiration for these temporary credentials is 12 hours; the minimum is 15 minutes, and the maximum is 36 hours.

  You can also use temporary credentials with Multi-Factor Authentication (MFA)-Protected API Access.

- What is the maximum size of the access policy that I can specify when requesting temporary security credentials (either GetFederationToken or AssumeRole)?

  The policy plaintext must be 2048 bytes or shorter. However, an internal conversion compresses it into a packed binary format with a separate limit.


- Can a temporary security credential be revoked prior to its expiration?

  No. When requesting temporary credentials, we recommend the following:

    - When creating temporary security credentials, set the expiration to a value that is appropriate for your application.
    - Because root account permissions cannot be restricted, use an IAM user and not the root account for creating temporary security credentials. You can revoke permissions of the IAM user that issued the original call to request it. This action almost immediately revokes privileges for all temporary security credentials issued by that IAM user

- Can I restrict the use of temporary security credentials to a region or a subset of regions?

    No. You cannot restrict the temporary security credentials to a particular region or subset of regions


Identity Federation
--

- What is identity federation?

  With identity federation, external identities are granted secure access to resources in your AWS account without having to create IAM users. These external identities can come from your corporate identity provider (such as Microsoft Active Directory or from the AWS Directory Service) or from a web identity provider (such as Amazon Cognito, Login with Amazon, Facebook, Google, or any OpenID Connect-compatible provider).

- How do I control how long a federated user has access to the AWS Management Console?

  Depending on the API used to create the temporary security credentials, you can specify a session limit between 15 minutes and 36 hours (for GetFederationToken and GetSessionToken) and between 15 minutes and 12 hours (for AssumeRole* APIs), during which time the federated user can access the console. When the session expires, the federated user must request a new session by returning to your identity provider, where you can grant them access again.

Billing
--
- Does the IAM service cost anything?

  No, this is a feature of your AWS account provided at no additional charge.

- Who pays for usage incurred by users under an AWS Account?

  The AWS account owner controls and is responsible for all usage, data, and resources under the account.

Additional questions
--

- What happens if a user tries to access a service that has not yet been integrated with IAM?

  The service returns an “Access denied” error.

IAM limits
--

**Default limits for IAM entities:**

<table>
  <tr>
    <th>Resource</th>
    <th>Default Limit</th>
  </tr>
  <tr>
    <td>Customer managed policies in an AWS account</td> 	<td>1500</td>
  </tr>
  <tr>
    <td>Groups in an AWS account</td>
    <td>300</td>
  </tr>
    <tr><td>Roles in an AWS account</td>
    <td>1000</td>
  </tr>
  <tr>
    <td>Users in an AWS account</td>
    <td>5000 (If you need to add a large number of users, consider using temporary security credentials.)</td>
  </tr>
  <tr>
    <td>Virtual MFA devices (assigned or unassigned) in an AWS account</td>
    <td>Equal to the user quota for the account</td>
  </tr>
  <tr>
    <td>Instance profiles in an AWS account</td>
    <td>1000</td>
  </tr>
  <tr>
    <td>Server certificates stored in an AWS account</td>
    <td>20</td>
    </tr>
<table>

**Limits for IAM entities**

<table>
  <tbody>
    <tr>
      <th>Resource</th>
      <th>Limit</th>
    </tr>
    <tr>
      <td>Access keys assigned to an IAM user</td>
      <td>2</td>
      </tr>
    <tr>
      <td>Access keys assigned to the AWS account root user</td>
      <td>2</td>
    </tr>
    <tr>
      <td>Aliases for an AWS account</td>
      <td>1</td>
    </tr>
    <tr>
      <td>Groups an IAM user can be a member of</td>
      <td>10</td>
    </tr>
    <tr>
      <td>IAM users in a group</td>
      <td>Equal to the user quota for the account</td>
    </tr>
    <tr>
      <td>Identity providers (IdPs) associated with an IAM SAML provider object</td>
      <td>10</td>
    </tr>
    <tr>
      <td>Keys per SAML provider</td>
      <td>10</td>
    </tr>
    <tr>
      <td>Login profiles for an IAM user</td>
      <td>1</td>
    </tr>
    <tr>
      <td>Managed policies attached to an IAM group</td>
      <td>10</td>
    </tr>
    <tr>
      <td>Managed policies attached to an IAM role</td>
      <td>10</td>
    </tr>
    <tr>
      <td>Managed policies attached to an IAM user</td>
      <td>10</td>
    </tr>
    <tr>
      <td>MFA devices in use by an IAM user</td>
      <td>1</td>
    </tr>
    <tr>
      <td>MFA devices in use by the AWS account root user</td>
      <td>1</td>
    </tr>
    <tr>
      <td>Roles in an instance profile</td>
      <td>1</td>
    </tr>
    <tr>
      <td>SAML providers in an AWS account</td>
      <td>100</td>
    </tr>
    <tr>
      <td>Signing certificates assigned to an IAM user</td>
      <td>2</td>
    </tr>
    <tr>
      <td>SSH public keys assigned to an IAM user</td>
      <td>5</td>
    </tr>
    <tr>
      <td>Versions of a managed policy that can be stored</td>
      <td>5</td>
    </tr>
  </tbody>
</table>

**IAM Entity Character Limits**


<table>
  <tbody>
    <tr>
      <th>Description</th>
      <th>Limit</th>
    </tr>
    <tr>
      <td>Path</td>
      <td>512 characters</td>
    </tr>
    <tr>
      <td>User name</td>
      <td>64 characters</td>
    </tr>
    <tr>
      <td>Group name</td>
      <td>128 characters</td>
    </tr>
    <tr>
      <td>Role name</td>
      <td>64 characters
        <div class="aws-note">
          <p class="aws-note">Important</p>
          <p>If you intend to use a role with the Switch Role feature in the AWS console,
          then the combined <code class="code">Path</code> and <code class="code">RoleName</code> cannot exceed 64
          characters.
          </p>
        </div>
      </td>
    </tr>
    <tr>
      <td>Instance profile name</td>
      <td>128 characters</td>
    </tr>
    <tr>
      <td>
        <p>Unique IDs created by IAM, for example:</p>
        <div class="itemizedlist">
          <ul class="itemizedlist" type="disc">
            <li class="listitem">
              <p>User IDs that begin with <code class="code">AIDA</code></p>
            </li>
            <li class="listitem">
              <p>Group IDs that begin with <code class="code">AGPA</code></p>
            </li>
            <li class="listitem">
              <p>Role IDs that begin with <code class="code">AROA</code></p>
            </li>
            <li class="listitem">
              <p>Managed policy IDs that begin with <code class="code">ANPA</code></p>
            </li>
            <li class="listitem">
              <p>Server certificate IDs that begin with <code class="code">ASCA</code></p>
            </li>
          </ul>
        </div>
        <div class="aws-note">
          <p class="aws-note">Note</p>
          <p>This is not intended to be an exhaustive list, nor is it a guarantee that IDs of
          a certain type begin only with the specified letter combination.</p>
        </div>
      </td>
      <td>128 characters</td>
    </tr>
    <tr>
      <td>Policy name</td>
      <td>128 characters</td>
    </tr>
    <tr>
      <td>Password for a login profile</td>
      <td>1 to 128 characters</td>
    </tr>
    <tr>
      <td>Alias for an AWS account ID</td>
      <td>3 to 63 characters</td>
    </tr>
    <tr>
      <td>Role trust policy JSON text (the policy that determines who is allowed to assume the role)
      </td>
      <td>2,048 characters</td>
    </tr>
    <tr>
      <td>Role session name</td>
      <td>64 characters</td>
    </tr>
    <tr>
      <td>For inline policies</td>
      <td>
        You can add as many inline policies as you want to an IAM user, role, or group, but the total aggregate policy size (the sum size of all inline policies) per entity cannot exceed the following limits:
        <div class="itemizedlist">
          <ul class="itemizedlist" type="disc">
            <li class="listitem">
              <p>User policy size cannot exceed 2,048 characters</p>
            </li>
            <li class="listitem">
              <p>Role policy size cannot exceed 10,240 characters</p>
            </li>
            <li class="listitem">
              <p>Group policy size cannot exceed 5,120 characters</p>
            </li>
          </ul>
        </div>
        <div class="aws-note">
          <p class="aws-note">Note</p>
          <p>IAM does not count whitespace when calculating the size of a policy against these limitations.
          </p>
        </div>
      </td>
    </tr>
    <tr>
      <td>For managed policies</td>
      <td>
        <div class="itemizedlist">
          <ul class="itemizedlist" type="disc">
            <li class="listitem">
              <p>You can add up to 10 managed policies to an IAM user, role, or group.</p>
            </li>
            <li class="listitem">
              <p> The size of each managed policy cannot exceed 6,144 characters. </p>
            </li>
          </ul>
        </div>
        <div class="aws-note">
          <p class="aws-note">Note</p>
          <p>IAM does not count whitespace when calculating the size of a policy against this limitation.
          </p>
        </div>
      </td>
    </tr>
  </tbody>
</table>



Multi-Factor Authentication
--

- What is AWS MFA?

  AWS multi-factor authentication (AWS MFA) provides an extra level of security that you can apply to your AWS environment. You can enable AWS MFA for your AWS account and for individual AWS Identity and Access Management (IAM) users you create under your account.

- Can I have multiple authentication devices active for my AWS account?

  Yes. Each IAM user can have its own authentication device. However, each identity (IAM user or root account) can be associated with only one authentication device.

- Can I use my authentication device with multiple AWS accounts?

  No. The authentication device or mobile phone number is bound to an individual AWS identity (IAM user or root account). If you have a TOTP-compatible application installed on your smartphone, you can create multiple virtual MFA devices on the same smartphone.
