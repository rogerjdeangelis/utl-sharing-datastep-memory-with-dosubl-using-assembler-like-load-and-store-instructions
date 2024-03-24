# utl-sharing-datastep-memory-with-dosubl-using-assembler-like-load-and-store-instructions
Sharing parent datastep main memory storage with dosubl by defining a block of common storage
    %let pgm=utl-sharing-datastep-memory-with-dosubl-using-assembler-like-load-and-store-instructions;

    SAS allows peek and poke, which are alias's for the powerfull assembler load and store instructions.

    Sharing parent datastep main memory storage with dosubl by defining a block of common storage.

    Problem
      Call dosubl to square variable vales that are stored in a common block of storage

    The COMMON[type] macro defines a block of main memory storage shared with dosubl.
    This provides the sharing of data without using arguments.

    Macro common[n]  shares numeric data and common[c] shares character data.

    The size of the block of shared main memory must be the same in parent and dosubl.

    github
    https://tinyurl.com/36kc2w68
    https://github.com/rogerjdeangelis/utl-sharing-datastep-memory-with-dosubl-using-assembler-like-load-and-store-instructions

    Related repos on end

    /*
     _ __  _ __ ___   ___ ___  ___ ___
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    */

    data squares;

       /*---- initiialize the block of main storage to share                 ----*/
       /*---- pass starting address of the block storage length 8 bytes      ----*/
       /*---- the address is stored macro variable in character hex format   ----*/

       %commonn(num);

       do number=1 to 4;

          num=number; /*---- num is in common storage (like an argument)     ----*/

             /*---- call dosubl subroutine                                   ----*/
             rc=dosubl('
               data _null_;
                 /*---- like assembly load address instruction               ----*/
                 %commonn(num,action=GET);
                 num=num**2;
                 /*---- like assembly store address instruction              ----*/
                 %commonn(num,action=PUT);
               run;quit;
              ');

          square=num;
          output;
          drop num rc;
       end;
    run;quit;

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /* WORK.SQUARES total obs=4 24MAR2024:10:07:04                                                                            */
    /*                                                                                                                        */
    /* Obs    NUMBER    SQUARE                                                                                                */
    /*                                                                                                                        */
    /*  1        1         1                                                                                                  */
    /*  2        2         4                                                                                                  */
    /*  3        3         9                                                                                                  */
    /*  4        4        16                                                                                                  */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    REPO
    -----------------------------------------------------------------------------------------------------------------------------------------
    https://github.com/rogerjdeangelis/utl-twelve-interfaces-for-dosubl
    https://github.com/rogerjdeangelis/utl-potentially-useful-dosubl-interface
    https://github.com/rogerjdeangelis/utl_dosubl_subroutine_interfaces

    https://github.com/rogerjdeangelis/-utl-delete-dosubl-created-sas-macro-libraries
    https://github.com/rogerjdeangelis/Dynamic_variable_in_a_DOSUBL_execute_macro_in_SAS
    https://github.com/rogerjdeangelis/utl-DOSUBL-running-sql-inside-a-datastep-to-check-if-variables-exist-in-another-table
    https://github.com/rogerjdeangelis/utl-No-need-to-convert-your-datastep-code-to-macro-code-use-DOSUBL
    https://github.com/rogerjdeangelis/utl-a-better-call-execute-using-dosubl
    https://github.com/rogerjdeangelis/utl-academic-pipes-dosubl-open-defer-and-dropping-dowm-to-multiple-languages-in-one-datastep
    https://github.com/rogerjdeangelis/utl-adding-female-students-to-an-all-male-math-class-using-sql-insert_and_dosubl
    https://github.com/rogerjdeangelis/utl-adding-summary-statistics-to-your-datastep-input-table-macro-dosubl
    https://github.com/rogerjdeangelis/utl-append-and-split-tables-into-two-tables-one-with-common-variables-and-one-without-dosubl-hash
    https://github.com/rogerjdeangelis/utl-applying-meta-data-and-dosubl-to-create-mutiple-subset-tables
    https://github.com/rogerjdeangelis/utl-cleaner-macro-code-using-dosubl
    https://github.com/rogerjdeangelis/utl-dosubl-a-more-powerfull-macro-sysfunc-command
    https://github.com/rogerjdeangelis/utl-dosubl-and-do-over-as-alternatives-to-explicit-macros
    https://github.com/rogerjdeangelis/utl-dosubl-more-precise-eight-byte-float-computations-at-macro-excecution-time
    https://github.com/rogerjdeangelis/utl-dosubl-persistent-hash-across-datasteps-and-procedures
    https://github.com/rogerjdeangelis/utl-dosubl-remove-text-within-parentheses-of-macro-variable-using-regex
    https://github.com/rogerjdeangelis/utl-dosubl-using-meta-data-with-column-names-and-labels-to-create-mutiple-proc-reports
    https://github.com/rogerjdeangelis/utl-drop-down-using-dosubl-from-sas-datastep-to-wps-r-perl-powershell-python-msr-vb
    https://github.com/rogerjdeangelis/utl-embed-sql-code-inside-proc-report-using-dosubl
    https://github.com/rogerjdeangelis/utl-embedding-dosubl-in-a-macro-and-returning-an-updated-environment-variable-contents
    https://github.com/rogerjdeangelis/utl-error-checking-sql-and-executing-a-datastep-inside-sql-dosubl
    https://github.com/rogerjdeangelis/utl-extracting-sas-meta-data-using-sas-macro-fcmp-and-dosubl
    https://github.com/rogerjdeangelis/utl-get-dataset-attributes-at-macro-time-within-a-datastep-using-attrn-dosubl-macros
    https://github.com/rogerjdeangelis/utl-in-memory-hash-output-shared-with-dosubl-hash-subprocess
    https://github.com/rogerjdeangelis/utl-let-dosubl-and-the-sas-interpreter-work-for-you
    https://github.com/rogerjdeangelis/utl-load-configuation-variable-assignments-into-an-sas-array-macro-and-dosubl
    https://github.com/rogerjdeangelis/utl-loop-through-one-table-and-find-data-in-next-table--hash-dosubl-arts-transpose
    https://github.com/rogerjdeangelis/utl-macro-klingon-solution-or-simple-dosubl-you-decide
    https://github.com/rogerjdeangelis/utl-macro-with-dosubl-to-compute-last-day-of-month
    https://github.com/rogerjdeangelis/utl-maitainable-macro-function-code-using-dosubl
    https://github.com/rogerjdeangelis/utl-passing-a-datastep-array-to-dosubl-squaring-the-elements-passing-array-back-to-parent
    https://github.com/rogerjdeangelis/utl-re-ordering-variables-into-alphabetic-order-in-the-pdv-macros-dosubl
    https://github.com/rogerjdeangelis/utl-rename-variables-with-the-same-prefix-dosubl-varlist
    https://github.com/rogerjdeangelis/utl-sas-array-macro-fcmp-or-dosubl-take-your-choice
    https://github.com/rogerjdeangelis/utl-select-high-payment-periods-and-generating-code-with-do_over-and-dosubl
    https://github.com/rogerjdeangelis/utl-some-interesting-applications-of-dosubl
    https://github.com/rogerjdeangelis/utl-transpose-multiple-rows-into-one-row-do_over-dosubl-and-varlist-macros
    https://github.com/rogerjdeangelis/utl-use-dosubl-to-save-your-format-code-inside-proc-report
    https://github.com/rogerjdeangelis/utl-using-dosubl-and-a-dynamic-arrays-to-add-new-variables
    https://github.com/rogerjdeangelis/utl-using-dosubl-to-avoid-klingon-obsucated-macro-coding
    https://github.com/rogerjdeangelis/utl-using-dosubl-to-avoid-macros-and-add-an-error-checking-log
    https://github.com/rogerjdeangelis/utl-using-dosubl-to-exceute-r-for-each-row-in-a-dataset
    https://github.com/rogerjdeangelis/utl-using-dosubl-with-data-driven-business-rules-to-split-a-table
    https://github.com/rogerjdeangelis/utl-using-dynamic-tables-to-interface-with-dosubl
    https://github.com/rogerjdeangelis/utl_avoiding_macros_and_call_execute_by_using_dosubl_with_log
    https://github.com/rogerjdeangelis/utl_dosubl_do_regressions_when_data_is_between_dates
    https://github.com/rogerjdeangelis/utl_dosubl_macros_to_select_max_value_of_a_column_at_datastep_execution_time
    https://github.com/rogerjdeangelis/utl_dynamic_subroutines_dosubl_with_error_checking
    https://github.com/rogerjdeangelis/utl_overcoming_serious_deficiencies_in_call_execute_with_dosubl
    https://github.com/rogerjdeangelis/utl_pass_character_and_numeric_arrays_to_dosubl
    https://github.com/rogerjdeangelis/utl_passing-in-memory-sas-objects-to-and-from-dosubl
    https://github.com/rogerjdeangelis/utl_read_all_datasets_in_a_library_and_conditionally_split_them_with_error_checking_dosubl
    https://github.com/rogerjdeangelis/utl_sharing_a_block_of_memory_with_dosubl
    https://github.com/rogerjdeangelis/utl_using_dosubl_instead_of_a_macro_to_avoid_numeric_truncation
    https://github.com/rogerjdeangelis/utl_using_dosubl_to_avoid_klingon_macro_quoting_functions
    https://github.com/rogerjdeangelis/utl_why_proc_import_export_needs_to_be_deprecated_and_dosubl_acknowledged

    /*
      ___ ___  _ __ ___  _ __ ___   ___  _ __   ___
     / __/ _ \| `_ ` _ \| `_ ` _ \ / _ \| `_ \ / __|
    | (_| (_) | | | | | | | | | | | (_) | | | | (__
     \___\___/|_| |_| |_|_| |_| |_|\___/|_| |_|\___|

    */

    %macro commonc(var,action=INIT);
     * dosubl sets sysindex to 1;
     * we are in dosubl if sysindex=1;
     * increment sysindex so it is not 1 next time macro called;
     %local varcut varlen;
     %let varcut=%scan(&var,1);
     %let varlen=%scan(&var,2);
     %if %upcase(&action) = INIT %then %do;
        length &var;
        retain &varcut " ";
        call symputx("varadr",put(addrlong(&varcut.),hex16.),"G");

     %end;
     %if "%upcase(&action)" = "PUT" %then %do;
        length &var;
        retain &varcut;
        call pokelong(&varcut.,"&varadr."x, &varlen.);
     %end;
     %else %if "%upcase(&action)" = "GET" %then %do;

        retain &varcut " ";
        &varcut = peekclong("&varadr."x,&varlen.);
        %end;

    %mend commonc;
    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
