---
title: Can I prevent "external" toolboxes from being added to my MATLAB path?
tags: [faq, matlab, toolbox, path]
---

# Can I prevent "external" toolboxes from being added to my MATLAB path?

The recommended path settings are explained in this [frequently asked question](/faq/should_i_add_fieldtrip_with_all_subdirectories_to_my_matlab_path).

The code in the **[ft_defaults](https://github.com/fieldtrip/fieldtrip/blob/release/ft_defaults.m)** function will execute only once and should preferably be executed in your `startup.m` file. The main FieldTrip functions will also call **[ft_defaults](https://github.com/fieldtrip/fieldtrip/blob/release/ft_defaults.m)** to ensure that the required subdirectories are on the path.

The **[ft_defaults](https://github.com/fieldtrip/fieldtrip/blob/release/ft_defaults.m)** will also add some toolboxes from external to your path, such as external/signal, external/stats and external/image. These contain drop-in [replacements for some MATLAB functions](/faq/matlab_replacements) to reduce the requirements on the (network) licenses, which are often available in a limited number.

If you don't want these replacement functions on your path, you can do the following in your `startup.m` file.

    global ft_default
    ft_default.toolbox.signal = 'matlab';  % can be 'compat' or 'matlab'
    ft_default.toolbox.stats  = 'matlab';
    ft_default.toolbox.image  = 'matlab';
    ft_defaults % this sets up the FieldTrip path

Alternatively, to remove them at a later stage you can do the following

    [ftver, ftpath] = ft_version;
    rmpath(fullfile(ftpath, 'external', 'signal'))
    rmpath(fullfile(ftpath, 'external', 'stats'))
    rmpath(fullfile(ftpath, 'external', 'image'))
