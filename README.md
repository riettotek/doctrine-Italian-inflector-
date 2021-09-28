# doctrine-Italian-inflector-

## italian language for the pluraliazer

### Author: Mattias Raiani

This is a first step for the italian language for Inflector. I'll improve it in the future



#### SETTING
 Once u have installed the Doctrine Inflector (or Laravel project), you have to put the folder **Italian** in this path:
 ```
vendor/doctrine/inflector/lib/Doctrine/Inflector/Rules
 ```

#### USING
 When u use by your own u got to write:
```
use Doctrine\Inflector\InflectorFactory;
use Doctrine\Inflector\Language;

$inflector = InflectorFactory::createForLanguage(Language::ITALIAN)->build();
```
#### USING in LARAVEL
Then u have to change two lines of code. Find the file Pluraliazer.php in this path:
```vendor/laravel/framework/src/Illuminate/Support/Pluralizer.php```

Change the use statement:

   *use Doctrine\Inflector\Rules\English;*

in
```
use Doctrine\Inflector\Rules\Italian;
```
then, at the end of the file, change the last method, inserting the class "Italian/Rules" instead of "English/Rules" so like this:
```
    public static function inflector()
    {
        static $inflector;

        if (is_null($inflector)) {
            $inflector = new Inflector(
                new CachedWordInflector(new RulesetInflector(
                    Italian\Rules::getSingularRuleset()
                )),
                new CachedWordInflector(new RulesetInflector(
                    Italian\Rules::getPluralRuleset()
                ))
            );
        }

        return $inflector;
    }
```
