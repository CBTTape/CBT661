# CBT661
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. 
Due to amazing work by Alison Zhang and Jake Choi repos are no longer deleted.

```
//***FILE 661 is from Peter McFarland and contains his HOTRDR       *   FILE 661
//*           package to submit jobs to the internal reader from    *   FILE 661
//*           pds libraries.  More detailed documentation of the    *   FILE 661
//*           package follows:                                      *   FILE 661
//*                                                                 *   FILE 661
//*             Author:                                             *   FILE 661
//*             Peter McFarland                                     *   FILE 661
//*             ADP Tax & Financial Services                        *   FILE 661
//*             San Diego, CA. 92127                                *   FILE 661
//*             (858) 385-2718                                      *   FILE 661
//*             peter_mcfarland@adp.com                             *   FILE 661
//*                                                                 *   FILE 661
//*     HOTRDR documentation:                                       *   FILE 661
//*                                                                 *   FILE 661
//*     The HOTRDR routine was written to submit JCL members        *   FILE 661
//*     for batch processing to the internal reader from            *   FILE 661
//*     multiple PDS libaraies.  We use it as a started task        *   FILE 661
//*     to submit batch jobs during IPL time and through the        *   FILE 661
//*     daily workload processing by the operations staff.          *   FILE 661
//*                                                                 *   FILE 661
//*     Mulitple symbolic PDS libaraies (LRECL=80) may be           *   FILE 661
//*     concatenated on the PDS DD statement.  PDS libraries        *   FILE 661
//*     with a large block sizes work best and reduce the I/O       *   FILE 661
//*     activity (BLKSIZE=27920).  I have 6 large PDS               *   FILE 661
//*     libraries concatenated in our HOTRDR procedure              *   FILE 661
//*     currently and have no idea what the limit would be (we      *   FILE 661
//*     are currently at z/OS 1.2).                                 *   FILE 661
//*                                                                 *   FILE 661
//*     The JCL member name to be submitted is passed to the        *   FILE 661
//*     HOTRDR routine through the PARM field.  The first           *   FILE 661
//*     occurance of the JCL member name found in the PDS           *   FILE 661
//*     concatenation is the member submitted.  To avoid            *   FILE 661
//*     multiple JCL member names in the concatenation list we      *   FILE 661
//*     use a member naming convention based on the task to be      *   FILE 661
//*     performed, the first 3 characters of the member name,       *   FILE 661
//*     i.e. SYS for a systems task, BKU for a backup job, ADP      *   FILE 661
//*     for an application job, etc.                                *   FILE 661
//*                                                                 *   FILE 661
//*     The HOTRDR routine is written in IBM assembler              *   FILE 661
//*     (ASMA90) and uses the BSAM access method and macros         *   FILE 661
//*     FIND, READ, and CHECK.  See the source code comments        *   FILE 661
//*     for additional information on macro usage.                  *   FILE 661
//*                                                                 *   FILE 661
//*     The source library contains the following:                  *   FILE 661
//*                                                                 *   FILE 661
//*     $$README - this member.                                     *   FILE 661
//*     $CLEAR   - a macro to clear fields to a specified fill      *   FILE 661
//*                character. If LONG is specified a MVCL           *   FILE 661
//*                instruction is generated.                        *   FILE 661
//*     $EX      - a macro used to generate EX instructions on      *   FILE 661
//*                the fly.                                         *   FILE 661
//*     ASMARDR  - the JCL procedure to assemble and link the       *   FILE 661
//*                HOTDRDR source.                                  *   FILE 661
//*     CONVERT  - a macro to convert HEX fields to printable       *   FILE 661
//*                characters. I use this macro to print            *   FILE 661
//*                return and reason codes.                         *   FILE 661
//*     ESAENTRY - a macro for conventional assembly routine        *   FILE 661
//*                entry and obtaining a save/work area.            *   FILE 661
//*                Handy for rentrant code.                         *   FILE 661
//*     ESAEXIT  - a macro used in conjunction with the             *   FILE 661
//*                ESAENTRY macro to do save/work area              *   FILE 661
//*                clean-up and assembly routine exiting.           *   FILE 661
//*     HOTRDR   - the assembly source code for the HOTRDR          *   FILE 661
//*                routine.                                         *   FILE 661
//*     PARMS    - a macro to handle the passing of parm            *   FILE 661
//*                fields.                                          *   FILE 661
//*     WTOL     - a macro to issue WTO messages with variable      *   FILE 661
//*                fields within the message.                       *   FILE 661
//*                                                                 *   FILE 661
//*     Note:  Some of these macros are old and have not been       *   FILE 661
//*            revised over the years I've used them.  Most of      *   FILE 661
//*            them are downward compatable with earlier            *   FILE 661
//*            version of OS/390 (MVS).                             *   FILE 661
//*                                                                 *   FILE 661
```
