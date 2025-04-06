# wpcli-codes

Steps to be followed for linux:

1) Install WP CLI => 
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar

2) Check the Status =>
php wp-cli.phar --info

3) chmod +x wp-cli.phar => giving permission

4) sudo mv wp-cli.phar /usr/local/bin/wp => moving location 



On windows for xampp:

1) go to Htdocs

2) composer create-project wp-cli/wp-cli-bundle --prefer-source OR composer global require wp-cli/wp-cli-bundle

3) Now copy path D:\xampp\htdocs\wp-cli-bundle\vendor\wp-cli\wp-cli\bin as environment variable for globally understand WP command


For more, visit https://make.wordpress.org/cli/handbook/guides/installing/


On Mac :

1) brew install wp-cli

Now WP command is activated: 

1) wp --info


## TEST DRIVE COMMAND LIST


1) wp core download

2) wp config create --dbname=db_wpnepal --dbuser=wp --dbpass=securepswd4

3) wp db create // wp db drop --yes // wp db reset --yes  // wp db query < debug.sql

4) wp core install --url='http://localhost/testraj' --title='Test Rajan' --admin_user='testrajan' --admin_email='rajan.lama786@gmail.com' --admin_password='testrajan'

5) wp admin

6) wp package install wp-cli/admin-command => this will install package and activate admin command

7) Run admin command eg: wp admin --path=<path of wordpress folder>  => this will open 

8) wp theme list

9) wp plugin list OR wp plugin install html-tags-on-post-title OR wp plugin uninstall html-tags-on-post-title

10) wp theme update --all --exclude=twentyfifteen

11) wp embed fetch https://www.youtube.com/watch?v=dQw4w9WgXcQ

12) wp cron event schedule cron_test // wp cron event run --due-now // wp cron event delete cron_test

13) This is used to run php
wp eval 'echo WP_CONTENT_DIR;'

14) wp eval-file // Loads and executes a PHP file.  

17) wp plugin install redis-cache --activate // Now install cache plugin

18) wp cache flush //  wp cache delete my_key my_group

15) adding custom command with function

function WpNepalCommand( $args ) {
    WP_CLI::success( 'Thank you for visit Wordcamp Nepal 2025.' );
}
WP_CLI::add_command( 'wp-fn', 'WpNepalCommand' );

	
16) adding custom command with Class

class Wp_Nepal_Command {
    protected $environment;

    public function __construct( ) {
        $this->environment = wp_get_environment_type();
    }


    public function __invoke( $args ) {
        WP_CLI::log( sprintf( 'The current environment is: %s', $this->environment ) );
    }
}

// can use any approach

// 1. Register the instance for the callable parameter.
$instance = new Wp_Nepal_Command();
WP_CLI::add_command( 'wpn-env-check', $instance );

// 2. Register object as a function for the callable parameter.
WP_CLI::add_command( 'wpn-env-check', 'Wp_Nepal_Command' );

