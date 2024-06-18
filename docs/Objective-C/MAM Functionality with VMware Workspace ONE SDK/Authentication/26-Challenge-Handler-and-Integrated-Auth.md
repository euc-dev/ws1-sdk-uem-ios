---
layout: page
title: Challenge Handler and Integrated Authentication
hide:
  #- navigation
  - toc
---

On the Security Policies page, you can set Integrated Authentication to Enabled to allow the SSO credentials or a certificate to be passed on and used for authenticating into Web sites, such as content repositories (SharePoint) or wikis.

The Workspace ONE SDK for iOS (Objective-C) does not support the use of SCEP for handling certificates. Do not select SCEP options for certificate authorities for SDK implementations.

Once enabled, you must define a list of allowed sites, which are the only sites supported with Integrated Authentication.

On the application side, use the challenge handler component in the AWController class of the Workspace ONE SDK. Inside the AWController, use certain methods to handle an incoming authentication challenge for connections made with NSURLConnection and NSURLSession. Find the available methods in the list.

| Method | Description |
| --- | --- |
| * Objective-C<br>-(BOOL)canHandleProtectionSpace:<br>(NSURLProtectionSpace*)protectionSpace withError:(NSError**)error<br><br>* Swift<br>func canHandle(_ protectionSpace: URLProtectionSpace, withError error: Error?) -> Bool | Checks that the Workspace ONE SDK for iOS (Objective-C) has the means to handle this type of authentication challenge. The SDK makes several checks to determine that it can handle challenges.<br><br>1. Is the Web site challenging for authentication on the list of allowed sites in the SDK profile?<br>2. Is the challenge one of the supported types:<br>   * Basic<br>   * NTLM<br>   * Client certificate<br>3. Does the SDK have a set of credentials to respond with:<br>   * Certificate<br>   * User name and password<br><br>If all three of the criteria are met, then this method returns YES.<br><br>The SDK does not handle server trust, so your application must handle `NSURLAuthenticationMethodServerTrust`. |
| * Objective-C<br>-(BOOL)handleChallenge:<br>(NSURLAuthenticationChallenge*)challenge<br><br>* Swift<br>func handle(_ challenge:<br>URLAuthenticationChallenge) -> Bool | Responds to the actual authentication challenge from a network call made using NSURLConnection.<br>It returns YES or NO depending on if it can respond to the authentication challenge.<br>The system calls the canHandleProtectionSpace method in AWController first to validate that the system can process the challenge. |
| * Objective-C<br>-(BOOL)handleChallengeForURLSessionChallenge:<br>(NSURLAuthenticationChallenge *)challenge completionHandler:(void (^)(NSURLSessionAuthChallengeDisposition disposition, NSURLCredential *credential))completionHandler;<br><br>* Swift<br>func handleChallenge(forURLSessionChallenge challenge:<br>URLAuthenticationChallenge, completionHandler: @escaping (_ disposition: URLSession.AuthChallengeDisposition, _ credential: URLCredential) -> Void) -> Bool | Responds to the actual authentication challenge from a network call made using NSURLSession.<br><br>This method is the same as the handleChallenge method, except the system uses this method with calls made with NSURLSession. This call involves using a completion block to handle authentication challenges. |
| * Objective-C<br>-(void)fetchNewCertificatesWithError:(NSError**)error<br><br>Swift<br>func fetchNewCertificatesWithError(_ error: Error?) | Forces the SDK to fetch a new certificate.<br><br>The SDK automatically handles retrieving certificates initially during setup, after you call start in AWController. However, in the event you must force the SDK to fetch a new certificate, use this method.<br><br>Ensure that a certificate is properly configured in the authentication and credentials payload of the SDK profile.<br><br>This method resolves issues with revoked and corrupt certificates. |

Integrated authentication requires several configurations to work.
 
* The URL of the requested Web site must match an entry in your list of Allowed Sites.
* The system must make the network call so that the process provides an NSURLAuthenticationChallenge object.

* The Web site must return a 401 status code requesting authentication with one of the listed authentication methods.
   * NSURLAuthenticationMethodBasic
   * NSURLAuthenticationMethodNTLM
   * NSURLAuthenticationMethodClientCertificate
* The challenge handler can only use the enrollment credentials of the user when attempting to authenticate with a Web site. If a Web site requires a domain to log in, for example ACME\jdoe, and users enrolled with a basic user name, like jdoe, then the authentication fails.
* For applications using WebView, use the SDK's handleChallege method in the URLSession's challenge handler. Display the response on a UIWebView or a WKWebView. Do not use the SDK's handleChallenge method directly inside WKWebView's challenge handler.

## Content Repository Behavior

Content repositories use the saved enrollment credentials (which are encrypted and shared with all SSO apps). If the content repository requires a different password, the connecting app prompts the user for the password at the time of accessing the repository.

## Sample Code

This example illustrates how to handle a challenge from a network call made through NSURLConnection.

Note: This example is generic, so expand upon it in your application to handle errors and fallback scenarios.

```
- (void)connection:(NSURLConnection *)connection 
willSendRequestForAuthenticationChallenge:
(NSURLAuthenticationChallenge *)challenge{
	NSError*error;

 	if([[AWController clientInstance] 
	canHandleProtectionSpace:challenge.protectionSpace 
	withError:&amp;error]){
 		
		if([[AWController clientInstance] 
		handleChallenge:challenge]){

			NSLog(@"Challenge handled successfully");
 
		}else{

			NSLog(@"Challenge could not be handled");
		}

	}else{
		//SDK does not have the means to handle this 
		authentication. Add your own fallback and SSL logic 
		here.

	}
} 
```
