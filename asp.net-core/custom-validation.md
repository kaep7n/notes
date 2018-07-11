# custom validation

## property attributes

to implement a custom validation attribute override the 'IsValid' method of the base class 'ValidationAttribute'

```csharp
  public class RequiredLanguagesAttribute : ValidationAttribute
    {
        private readonly string[] requiredLanguages;

        public RequiredLanguagesAttribute(params string[] requiredLanguages)
        {
            this.requiredLanguages = requiredLanguages;
        }

        protected override ValidationResult IsValid(object value, ValidationContext validationContext)
        {
            var tranlatableString = value as TranslatableString;

            if (tranlatableString == null)
            {
                return new ValidationResult($"Value is not from type {typeof(TranslatableString)}");
            }

            foreach (var requiredLanguage in this.requiredLanguages)
            {
                if (!tranlatableString.ContainsKey(requiredLanguage))
                {
                    return new ValidationResult($"Required language '{requiredLanguage}' must be provided");
                }

                var translatedValue = tranlatableString[requiredLanguage];

                if (string.IsNullOrEmpty(translatedValue))
                {
                    return new ValidationResult($"Required language '{requiredLanguage}' value must not be null or empty");
                }
            }

            return ValidationResult.Success;
        }
    }
```

{% hint style="info" %}
The 'RequiredLangaugesAttribute' checks if a Translatable String \(which is a Dictionary&lt;string,string&gt;\) contains a specific key \(language\) and a value to this key that is not null or empty.
{% endhint %}

after implementing the attribute add it to the given property

```csharp
public class Document : Entity
{
    [Required]
    public string CatalogVersionId { get; set; }

    [RequiredLanguages("en-US")]
    public TranslatableString Name { get; set; }

    public TranslatableString Description { get; set; }

    [Required]
    public string DocumentTypeId { get; set; }

    public Language Language { get; set; }

    [Required]
    public string XmlFrame { get; set; }

    public bool IsDeleted { get; set; }
}
```

## interface IValidateableObject

implement this interface for specific object validations

```csharp
public class Document : IValidatableObject
{
    public string XmlFrame { get; set; }

    public IEnumerable<ValidationResult> Validate(ValidationContext validationContext)
    {
        if (!this.XmlFrame.Contains("%ProductsPlaceholder%"))
        {
            yield return new ValidationResult("Xml Frame does not contain required placeholder %ProductsPlaceholder%", new[] { "XmlFrame" });
        }
    }
}
```



