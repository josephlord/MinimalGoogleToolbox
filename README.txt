Minimal Google Toolbox is derived from Google Toolbox of Mac Release Notes

This is a minimal and personal selection from the Google Toolbox for the use and
needs of Human Friendly Ltd.  As with the original it is available under the
Apache 2 License.

It is expected to be a pure subset of the Google Toolkit that represents the
elements that will be used in the project to minimise the application size and
without the application becoming a derived work.  It will only be updated if or
when Human Friendly Ltd.'s requirements change.

If you choose to use it you can build this project and then drag the resulting
Product 'libMinimalGoogleToolbox.a' into your application project.  You will also
need to copy in the header file "GTMNSString+HTML.h".  I believe that if you
follow this process your application will not be a derivative work under the
Apache2 license (as it will be linked so attribution rules need not
apply).  I am not a lawyer and this is not legal advice!

    "For the purposes of this License, Derivative Works shall not include works
    that remain separable from, or merely link (or bind by name) to the
    interfaces of, the Work and Derivative Works thereof."

If anyone has a different legal understanding of the intent of the Apache 2
license please let me know joseph@human-friendly.com.  I fully intend to comply
with the license and believe I am doing so but I'm open to changing the current
behaviour if required.

It should also be possible to drag this project into an your application as a
dependent product although I don't know if this may have a different legal
standing.

Currently this project only includes the HTML related string functions found in:
GTMNSString+HTML.m

/// Utilities for NSStrings containing HTML
@interface NSString (GTMNSStringHTMLAdditions)

/// Get a string where internal characters that need escaping for HTML are escaped 
//
///  For example, '&' become '&amp;'. This will only cover characters from table
///  A.2.2 of http://www.w3.org/TR/xhtml1/dtds.html#a_dtd_Special_characters
///  which is what you want for a unicode encoded webpage. If you have a ascii
///  or non-encoded webpage, please use stringByEscapingAsciiHTML which will
///  encode all characters.
///
/// For obvious reasons this call is only safe once.
//
//  Returns:
//    Autoreleased NSString
//
- (NSString *)gtm_stringByEscapingForHTML;

/// Get a string where internal characters that need escaping for HTML are escaped 
//
///  For example, '&' become '&amp;'
///  All non-mapped characters (unicode that don't have a &keyword; mapping)
///  will be converted to the appropriate &#xxx; value. If your webpage is
///  unicode encoded (UTF16 or UTF8) use stringByEscapingHTML instead as it is
///  faster, and produces less bloated and more readable HTML (as long as you
///  are using a unicode compliant HTML reader).
///
/// For obvious reasons this call is only safe once.
//
//  Returns:
//    Autoreleased NSString
//
- (NSString *)gtm_stringByEscapingForAsciiHTML;

/// Get a string where internal characters that are escaped for HTML are unescaped 
//
///  For example, '&amp;' becomes '&'
///  Handles &#32; and &#x32; cases as well
///
//  Returns:
//    Autoreleased NSString
//
- (NSString *)gtm_stringByUnescapingFromHTML;