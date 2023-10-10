---
title: Change / Disable the Easy Digital Download renewal discount if the license key expired
layout: post
tags:
  - Easy Digital Download
  - E-Commerce
---

In Easy Digital Download plugin, there is an option to offer a discount when someone renews their order.

There is option to set discounts globally or for each download. But this renewal discount is always available for all renewal. But in one of my client's store, he decided to remove this discount offer if the related license key is expired.

The solution is given below. You have to use this code snippet in your child theme's `functions.php` file.

    function th25r_edd_change_discount_after_license_expires( $renewal_discount, $license_id ) {
       $license = edd_software_licensing()->get_license( $license_id );
       if ( ! is_object( $license ) ) {
          // This can happen during purchase where the license ID is not yet valid
          return $renewal_discount;
       }
       if ( $license->is_expired() ) {
          $renewal_discount = 0; 
       }
       return $renewal_discount;
    }
    add_filter( 'edd_sl_renewal_discount_percentage', 'th25r_edd_change_discount_after_license_expires', 10, 2 );




