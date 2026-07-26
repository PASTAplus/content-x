# How to Create API Access Keys

[TOC]

## Steps

API Access Keys are simple to create and require just a few steps:

### 1. Sign-in

Sign-in to [IAM](https://auth.edirepository.org) with the identity provider of your choice.

<img class="screen-shot" src="/static/images/IAM-Sign-In.png" width="95%"> 

### 2. Select Profile menu > "Access Keys"

Once signed-in, select the *Profile menu* (the avatar button top-right), then select "Access Keys".

<img class="screen-shot" src="/static/images/IAM-Avatar.png" width="95%">

### 3. Select "New Key"

Your *Access Keys* page will display any access keys you have already created or an empty page with a "New Key" button. Select "New Key".

<img class="screen-shot" src="/static/images/IAM-AK-new-key.png" width="95%">

### 4. Enter Key Information

Selecting "New Key" opens the "Create a new access key" pop-up window:

1. Enter a descriptive key name in the field provided. While key names can be any text, using the name of the associated project or data package can help keep your keys organized.
1. In the "Principal" drop-down, select either your _Profile_ or a _Group_ (if one exists).
1. Assigning an access key to your _Profile_ grants full access equal to logging in directly with your identity provider. Assigning an access key to a _Group_ restricts its access strictly to the data packages explicitly permitted for that group.
1. "Duration" sets the valid lifespan of the access key. While access keys cannot be set to expire indefinitely, you can configure them to remain active for multiple years. You can keep the default 1-year lifespan or adjust it to a timeframe that suits your needs.
1. Once you are comfortable with the access key settings, select "Add." This will generate a new access key for you, along with the secret key identifier, which will be displayed in a follow-on pop-up window.

The **"Save your new key"** pop-up will display your secret key identifier. Copy the identifier—using either the copy button (<svg class="icon-char" viewBox="0 0 16 16">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z" />
    <path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z" />
  </svg>) or by highlighting the text and using your browser copy command—and store it in a secure location. This is the only time your complete secret key identifer will be shown.

Once you have securely saved your secret key identifier select "I have saved my key". Your new key will be displayed, along with any other keys you have previously created.

<video class="screen-shot" autoplay loop muted playsinline width="95%">
    <source src="/static/images/IAM-AK-Create-New-Key.webm" type="video/webm">
</video>


## Editing your access key

Any previously created access key may be edited, including deleted, by selecting the edit button (<svg class="icon-char" viewBox="0 0 512 512">
    <path d="M498.125,92.38l-78.505-78.506c-18.496-18.497-48.436-18.5-66.935,0C339.518,27.043,50.046,316.516,44.525,322.035c-2.182,2.182-3.725,4.918-4.46,7.915L0.502,491.068c-3.036,12.368,8.186,23.44,20.431,20.432c8.361-2.053,153.718-37.747,161.117-39.564c2.996-0.735,5.734-2.278,7.915-4.46c5.816-5.816,293.677-293.677,308.161-308.161C516.622,140.818,516.627,110.879,498.125,92.38z M39.957,472.043l1.612-6.562l4.951,4.951L39.957,472.043z M84.874,461.014l-33.887-33.887l14.736-60.009l79.16,79.16L84.874,461.014z M178.022,431.647l-97.668-97.668L332.559,81.773l97.668,97.668L178.022,431.647z M474.24,135.429l-19.508,19.507l-97.667-97.668l19.507-19.507c5.294-5.293,13.867-5.298,19.163,0l78.506,78.507C479.536,121.563,479.536,130.132,474.24,135.429z"/>
  </svg>) for the key you would like modify. Editing the access key will also display basic information, including creation and update dates, when the access key was last used, and how many times it has been used.

<img class="screen-shot" src="/static/images/IAM-AK-edit.png" width="95%">

To save any edits, select "Update." You may also delete your access key by selecting "Delete." Deleting an access key is permanent, so please be certain.

<img class="screen-shot" src="/static/images/IAM-AK-edit-pop-up.png" width="95%">
