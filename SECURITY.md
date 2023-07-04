# Security Policy

## Supported Versions

Use this section to tell people about which versions of your project are
currently being supported with security updates.

| Version | Supported          |
| ------- | ------------------ |
| 5.1.x   | :#✅_check_mark: |
| 5.0.x   | :x:                |
| 4.0.x   | :#✅_check_mark: |
| < 4.0   | :x:                |

## Reporting a Vulnerability

Use this section to tell people how to report a vulnerability.

Tell them where to go, how often they can expect to get an update on a
reported vulnerability, what to expect if the vulnerability is accepted or
declined, etc.
/**
 * Restrict access to the administration screens.
 *
 * Only administrators will be allowed to access the admin screens,
 * all other users will be shown a message instead.
 *
 * We do allow access for Ajax requests though, since these may be
 * initiated from the front end of the site by non-admin users.
 */
function restrict_admin() {

	if ( ! current_user_can( 'manage_options' ) && ( ! wp_doing_ajax() ) ) {
		wp_die( __( 'You are not allowed to access this part of the site' ) );
	}
}
add_action( 'admin_init', 'restrict_admin', 1 );
