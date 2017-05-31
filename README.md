# 1. Открываем консоль (нужна админка)
--------------------------------------
```sh
http://jira.eldorado.ru/plugins/servlet/scriptrunner/console?section=script_console
```

# 2. Вставляем следующий код.
---------------------------
```sh
import com.atlassian.jira.component.ComponentAccessor;
import com.atlassian.jira.issue.MutableIssue;
import java.sql.Timestamp;

MutableIssue issuee = ComponentAccessor.getIssueManager().getIssueByCurrentKey("Test-111"); // Номер задачи
issuee.setOriginalEstimate((long) (32*60*60)); // Оценка
issuee.setTimeSpent((long) 24*60*60); // Затрачено
issuee.setEstimate((long) 8*60*60); // Осталось
issuee.setCreated(new Timestamp(2017,5,26,8,0,0,0)); // Дата создания (год/месяц/день/часы/минуты/секунды/наносекунды)
issuee.setUpdated(new Timestamp(2017,5,26,8,0,0,0)); // Дата обновления (год/месяц/день/часы/минуты/секунды/наносекунды)
issuee.setAssignee("akrotov"); // Устанавливаем исполнителя
issuee.setReporter("akrotov"); // Устанавливаем автора
ComponentAccessor.getChangeHistoryManager().removeAllChangeItems(issuee); // Удалить историю
issuee.store(); // Применить изменения
```

# 3. Изменяем, что нужно и жмем run. (действия которые вам не нужны, можно удалить)
# 4. Solved!
